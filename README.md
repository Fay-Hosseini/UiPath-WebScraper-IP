````markdown

A UiPath automation bot that converts IP addresses in an Excel spreadsheet into **Country**, **Region**, and **City**, using browser automation on [whatismyipaddress.com](https://whatismyipaddress.com).

---

## 🚀 Features

- Reads IP addresses from an Excel file (`"IP"` column).  
- Opens Chrome/Edge for each IP to lookup location data.  
- Extracts **Country**, **Region**, and **City** via UI Automation.  
- Writes results back to Excel efficiently.  
- Includes error handling for failed IP lookups.

---

## 🛠 Prerequisites

- UiPath Studio 25.10.0 or later  
- Installed packages:  
  - `UiPath.Excel.Activities`  
  - `UiPath.System.Activities`  
  - `UiPath.UIAutomation.Activities`  
- Chrome or Edge browser installed.  
- An Excel file containing IP addresses under column `"IP"`.

---

## ⚡ Installation

1. Clone the repository:

```bash
git clone  https://github.com/Fay-Hosseini/UiPath-WebScraper-IP.git
````

2. Open `IP_Location_Extractor` in UiPath Studio.
3. Install missing dependencies via **Manage Packages** if prompted.

---

## 🎯 Usage

1. Place your input Excel file in a known location with an `"IP"` column.
2. Open `Main.xaml` in UiPath Studio.
3. Update the **Read Range** activity with the path to your Excel file.
4. Run the workflow.
5. The output Excel will contain `"Country"`, `"Region"`, and `"City"` columns filled in.

---

## 🗂 Workflow Overview

```
Main.xaml
 ├── Read Range (Excel → ipDataTable)
 ├── For Each Row in ipDataTable
 │     ├── Assign ipAddress = row("IP").ToString
 │     ├── Open Browser (Chrome/Edge)
 │     │     └── Navigate to https://whatismyipaddress.com/ip/ipAddress
 │     ├── Get Text → countryName
 │     ├── Get Text → regionName
 │     ├── Get Text → cityName
 │     ├── Close Browser
 │     ├── Assign row("Country") = countryName
 │     ├── Assign row("Region") = regionName
 │     └── Assign row("City") = cityName
 └── Write Range (Excel ← ipDataTable)
```

---

## ⚠️ Notes

* Browser automation is **slower** and more prone to breakage if the website layout changes.
* Add **Delays** to ensure pages load fully before scraping.
* Wrap browser activities in **Try/Catch** for robust error handling.

---

## 🤝 Contributing

1. Fork the repository.
2. Create a new branch:

```bash
git checkout -b feature-name
```

3. Make your changes and test your workflow.
4. Commit your changes:

```bash
git commit -m "Add description of changes"
```

5. Push to your branch and open a Pull Request.

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

```
