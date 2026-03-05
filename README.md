# PrestaSharp
### C# .NET client library for the PrestaShop API via web service

## What is this project?
**PrestaSharp** is a C# .NET client library that allows developers to interact with [PrestaShop](https://www.prestashop.com/) e-commerce stores programmatically through PrestaShop's built-in REST web service API.

[PrestaShop](https://www.prestashop.com/) is a free, open-source e-commerce platform used to build online stores. It exposes a REST web service that lets external applications read and write store data such as products, orders, customers, categories, and more.

PrestaSharp wraps this REST API in a clean, strongly-typed .NET library so you can manage your PrestaShop store data from any .NET application without dealing with raw HTTP requests or XML serialization.

## Introduction
A simple .NET REST client written in C# for the PrestaShop API.
PrestaSharp uses the [RestSharp](https://restsharp.dev/) library to consume the PrestaShop web services.

## Requirements
- .NET Framework 4.5 or higher
- [RestSharp](https://www.nuget.org/packages/RestSharp/) 105.0.1

## Installation

Install PrestaSharp via [NuGet](https://www.nuget.org/packages/PrestaSharp/):

```
PM> Install-Package PrestaSharp
```

Or via the .NET CLI:

```
dotnet add package PrestaSharp
```

## Basic usage
1) Initiate a client instance:

```
	string BaseUrl = "http://www.myweb.com/api";
	string Account = "ASDLKJOIQWEPROQWUPRPOQPPRQOW";
	string Password = "";
	ManufacturerFactory ManufacturerFactory = new ManufacturerFactory(BaseUrl, Account, Password);
```

2) Perform CRUD actions through the client:

```
	Bukimedia.PrestaSharp.Entities.manufacturer Manufacturer = ManufacturerFactory.Get(6);
	Manufacturer.name = "Iron Maiden";
	Manufacturer.active = 1;        
	ManufacturerFactory.Add(Manufacturer);
	ManufacturerFactory.Update(Manufacturer);
	ManufacturerFactory.Delete(Manufacturer);
```

3) Add an image:

```
	Bukimedia.PrestaSharp.Entities.product MyProduct = new Bukimedia.PrestaSharp.Entities.product()
	MyProduct = ProductFactory.Add(MyProduct)
	ImageFactory.AddProductImage((long)MyProduct.id, "C:\\MyImage.jpg");
```

## Advanced usage
1) Get all. This sample retrieves the list of manufacturers:

```
	List<manufacturer> manufacturers = ManufacturerFactory.GetAll();
```

2) Get ids. This sample retrieves the list of the manufacturer ids:

```
	List<long> ids = ManufacturerFactory.GetIds();
```

3) Get by filter. This sample retrieves the list of manufacturers which name is "Metallica":

```
	Dictionary<string, string> dtn = new Dictionary<string, string>();
	dtn.Add("name", "Metallica");
	List<manufacturer> manufacturers = ManufacturerFactory.GetByFilter(dtn, null, null);
```

4) Get by filter with wildcards. This sample retrieves the manufacturers which name starts with "Metall":

```
	Dictionary<string, string> dtn = new Dictionary<string, string>();
	dtn.Add("name", "[Metall]%");
	List<manufacturer> manufacturers = ManufacturerFactory.GetByFilter(dtn, null, null);
```

5) Get ids by filter. This sample retrieves the list of the manufacturers ids which name is "Metallica":

```
	Dictionary<string, string> dtn = new Dictionary<string, string>();
	dtn.Add("name", "Metallica");
	List<long> ids = ManufacturerFactory.GetIdsByFilter(dtn, null, null);
```

6) Get ids by filter with wildcards. This sample retrieves the list of the manufacturers ids which name starts with "Metall":

```
	Dictionary<string, string> dtn = new Dictionary<string, string>();
	dtn.Add("name", "[Metall]%");
	List<long> ids = ManufacturerFactory.GetIdsByFilter(dtn, null, null);
```

7) Get by complex filter. This sample retrieves the top five manufacturers in ascendent sorting which name starts with "Metall":

```
	Dictionary<string, string> dtn = new Dictionary<string, string>();
	dtn.Add("name", "[Metall]%");
	List<manufacturer> manufacturers = ManufacturerFactory.GetByFilter(dtn, "name_ASC", "5");
```

8) Get by filter for pagination. This sample retrieves the top five manufacturers from tenth position in ascendent sorting which name starts with "Metall":

```
	Dictionary<string, string> dtn = new Dictionary<string, string>();
	dtn.Add("name", "[Metall]%");
	List<manufacturer> manufacturers = ManufacturerFactory.GetByFilter(dtn, "name_ASC", "[9,5]");
```

## Supported resources
- Addresses
- Carriers
- Carts
- Categories
- Combinations
- Countries
- Currencies
- Customers
- Customer Messages
- Customer Threads
- Guests
- Groups
- Images
- Languages
- Manufacturers
- Orders
- Order Carriers
- Order Histories
- Order Payments
- Order States
- Products
- Product Features
- Product Feature Values
- Product Options
- Product Option Values
- Shops
- Specific Prices
- States
- Stock Availables
- Suppliers
- Tags
- Tax
- Tax Rules
- Tax Rule Groups
- Zones

## Supported actions
- Create
- Read
- Update
- Delete

## Roadmap
- Add other resources

## License
PrestaSharp is GNU General Public License (GPL)

This program is distributed in the hope that it will be useful, but without any warranty; without even the implied warranty of merchantabilty or fitness for a particular purpose. See the GNU General Public License for more details. You should have received a copy of the GNU General Public License along with this program. If not, see <http://www.gnu.org/licenses/>.

Bukimedia reserves the right to mention of companies or individuals who use this software.

Copyright (C) 2015 Bukimedia
- Bukimedia: http://www.bukimedia.com/
- Twitter: http://twitter.com/bukimedia
- GitHub: https://github.com/bukimedia
- PrestaSharp on Bukimedia: http://www.bukimedia.com/es/descargas/prestasharp