config/application.rb
```ruby
require 'csv'
```
index.hml.erb
```ruby
<p>
  Download:
  <%= link_to "CSV", products_path(format: "csv") %> |
  <%= link_to "Excel", products_path(format: "xls") %>
</p>
```
products_controller.rb
```ruby
def index
  @products = Product.order(:name)
  respond_to do |format|
    format.html
    format.csv { send_data @products.to_csv }
    format.xls # { send_data @products.to_csv(col_sep: "\t") }
  end
end
```
models/product.rb
```ruby
def self.to_csv(options = {})
  CSV.generate(options) do |csv|
    csv << column_names
    all.each do |product|
      csv << product.attributes.values_at(*column_names)
    end
  end
end
```
config/initializers/mime_types.rb
```ruby
Mime::Type.register "application/xls", :xls
```
views/products/index.xls.erb
```ruby
<?xml version="1.0"?>
<Workbook xmlns="urn:schemas-microsoft-com:office:spreadsheet"
  xmlns:o="urn:schemas-microsoft-com:office:office"
  xmlns:x="urn:schemas-microsoft-com:office:excel"
  xmlns:ss="urn:schemas-microsoft-com:office:spreadsheet"
  xmlns:html="http://www.w3.org/TR/REC-html40">
  <Worksheet ss:Name="Sheet1">
    <Table>
      <Row>
        <Cell><Data ss:Type="String">ID</Data></Cell>
        <Cell><Data ss:Type="String">Name</Data></Cell>
        <Cell><Data ss:Type="String">Release Date</Data></Cell>
        <Cell><Data ss:Type="String">Price</Data></Cell>
      </Row>
    <% @products.each do |product| %>
      <Row>
        <Cell><Data ss:Type="Number"><%= product.id %></Data></Cell>
        <Cell><Data ss:Type="String"><%= product.name %></Data></Cell>
        <Cell><Data ss:Type="String"><%= product.released_on %></Data></Cell>
        <Cell><Data ss:Type="Number"><%= product.price %></Data></Cell>
      </Row>
    <% end %>
    </Table>
  </Worksheet>
</Workbook>
```
