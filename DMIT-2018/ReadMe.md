# Lesson Plans

| Week | Monday | Tuesday | Thursday |
|:----:|--------|---------|----------|
|  1   | [W01-D1](#w01d1) | [W01-D2](#w01d2) | [W01-D3](#w01d3) |
|  2   | [W02-D1](#w02d1) | [W02-D2](#w02d2) | [W02-D3](#w02d3) |
|  3   | [W03-D1](#w03d1) | [W03-D2](#w03d2) | [W03-D3](#w03d3) |
|  4   | [W04-D1](#w04d1) | [W04-D2](#w04d2) | [W04-D3](#w04d3) |
|  5   | [W05-D1](#w05d1) | [W05-D2](#w05d2) | [W05-D3](#w05d3) |
|  6   | [W06-D1](#w06d1) | [W06-D2](#w06d2) | [W06-D3](#w06d3) |
|  7   | [W07-D1](#w07d1) | [W07-D2](#w07d2) | [W07-D3](#w07d3) |
|  8   | [W08-D1](#w08d1) | [W08-D2](#w08d2) | [W08-D3](#w08d3) |
|  9   | [W09-D1](#w09d1) | [W09-D2](#w09d2) | [W09-D3](#w09d3) |
|  10  | [W10-D1](#w10d1) | [W10-D2](#w10d2) | [W10-D3](#w10d3) |
|  11  | [W11-D1](#w12d1) | [W11-D2](#w11d2) | [W11-D3](#w11d3) |
|  12  | [W12-D1](#w12d1) | [W12-D2](#w12d2) | [W12-D3](#w12d3) |
|  13  | [W13-D1](#w13d1) | [W13-D2](#w13d2) | [W13-D3](#w13d3) |
|  14  | [W14-D1](#w14d1) | [W14-D2](#w14d2) | [W14-D3](#w14d3) |
|  15  | [W15-D1](#w15d1) | [W15-D2](#w15d2) | [W15-D3](#w15d3) |

---

## W01D1

> No Classes

---


## W01D2 

---


## W01D3 

---


## W02D1 

- Git from the Command Line


---


## W02D2 

- EF6-Recap

---


## W02D3 

- Northwind Traders - Practice Setup
  - Install database
  - Solution w. Web App & 2 class libraries
  - Update NuGet packages + Fix navigation
  - Add the ERD image
  - Code the Entities from scratch
  - Code the DAL
  - Code the BLL for CRUD
  - Create some CRUD pages

---


## W03D1 

- **Northwind Traders Practice**
  - Demo working **Manage Products** (from homework)
  - Create **CustomersListing**
    - Link to Page in Menu
    - ObjectDataSource
    - GridView
      - Error when rendering Navigation Properties - How to fix!
        - Remove the column, OR
        - `.Include(nameof(Customer.Orders))`
    - Customized GridView
      - GridView Formatting Headers
      - Fewer Columns - Remove **Demographics** and **LastModified** and **Orders**
      - Column Formatting
      - Template Column
        - Group contact info
        - Group Address info
        - Hidden field for the **OrderCount**
          - `.Include(nameof(Customer.Orders))`
    - Read Item from GridView
      - Set **`KeyNames`** to `CustomerID`
      - Selecting a line from the GridView and showing contents

---

## W03D2 

- **Northwind Traders Practice**
  - (cont.) Create **CustomersListing**
    - Filter Customers by company name
      - TextBox feeding ObjectDataSource feeding GridView
    - Debugging
    - Reverse-Engineer Entities/DAL
- ***Homework Practice***

  ```markdown
  Create a new page in the `~\CRUDReview\Databound\` folder called **Inventory.aspx**. Add the following features:

  - [ ] List all the Products in the database
  - [ ] Customize the GridView (column headings, template columns, etc)
  - [ ] Add a "Show Details" button that will grab info from the GridView to display in a label
  - [ ] Add the ability to search/filter by a *partial* product name
  ```


---

## W03D3 

- **Northwind Traders**
  - Demonstrate the problems with CRUD approach (Customer Purchase)

    ```
    Hello Mr. Lebihan, how can I help you today?
    Certainly, I can place that order for you. Can you tell me the name of your company? "Bon app'"? Wonderful! Let me start that order for you.
    When do you need the item? [Date] And is the shipping address the same as your business? Yes it is? Thank you, just a moment.
    ```

  - Ask what a good user interface should contain
- **Application Design Concerns**
  - User Interfaces should be **business focused** (not *database-focused*)
  - The BLL should be the "entry point" to the business processing of the system
    - The BLL is concerned with **transational integrity** and following the business rules
    - The UI layer should only be concerned with UI layer stuff, not "backend" processing.
    - Demonstrate how our current DAL/Entities can be called directly from our code-behind.
- **Chinook**
  - Demo Reverse Engineer Entities/DAL
  - Sample GridView of Employee Contacts under the `~/Contact.aspx` page (call *Context* class in page code-behind).
- **Take-Home Exercises** - Repository Setup

---


## W04D1 

- **Chinook**
  - POCOs and Internal
    - Preventing the exposure of DAL/Entities to PL
  - **ListView** (CRUD-like)
    - Albums w. Artist Name
  - **Nested Repeaters**
    - PlayList
    - Playlist Tracks
- **Take-Home Exercises** - Classroom Assignment

---

## W04D2 

- **Chinook**
  - **ListView** (CRUD-like)
    - CRUD Albums
      - Drop-Down Info for Insert/Edit

---

## W04D3 

- **Chinook**
  - **MessageUserControl**
  - **ListView** (CRUD-like)
    - SelectedItemTemplate
      - show Tracks
      - Nested Repeater
- **LinqPad**
  - Exploring Databases w. LinqPad
- **Practice**
  - Manage Tracks/Songs

---


## W05D1 

- **Questions** from previous classes
  - ODS to Drop-Down
  - Paging


????????????????
  - **Nested Repeaters**
    - PlayList for the tracks
    - Playlist Tracks
- **Practice**
  - Chinook
    - Media Types w. nested Tracks
    - Genres w. Tracks
  - Northwind
    - Show Products by Category - `ProductCatalog.aspx` - from Jan-2018
      - ListView inside Repeater


---


## W05D2 

---


## W05D3 

---


## W06D1 

> Thanksgiving Monday

---

## W06D2 

> LINQ

- Grouping

---

## W06D3 

> LINQ

- Grouping
  - **Practice**
    - **15.a** - Show all the products grouped by the supplier's country. I want to see the name of the product, the quantity per unit and unit price, and the company name of the supplier. (Hint: Start your query from the **Products** table)
    - **15.c** - Show all the sold products grouped by the customer's country. Show the product name and the customer's company name. (Hint: Start your query from the **OrderDetails** table)
    - Show all the sold products grouped by the country *to which they are shipped*. Show the product name and the customer's company name. (Hint: Start your query from the **OrderDetails** table)
- Aggregates

---


## W07D1 

- LINQ Method Syntax

---


## W07D2 

- Under-the-hood
  - Extension Methods

---


## W07D3 

---


## W08D1 

---


## W08D2 

![](../../SongListings.png)

---


## W08D3 

---


## W09D1 

---


## W09D2 

---


## W09D3 

---


## W10D1 

---


## W10D2 

---


## W10D3 

---


## W11D1 

---


## W11D2 

---


## W11D3 

---


## W12D1 

---


## W12D2 

---


## W12D3 

---


## W13D1 

---


## W13D2 

---


## W13D3 

---


## W14D1 

---


## W14D2 

---


## W14D3 

---


## W15D1 

---


## W15D2 

---


## W15D3 

