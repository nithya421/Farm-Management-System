FARM MANAGEMENT SYSTEM (FMS) — COMPLETE SALESFORCE PROJECT BUILD PROMPT

ROLE
Act as a senior Salesforce Developer and Salesforce Administrator. Complete the Farm Management System (FMS) described in the supplied project document. Build a clean, working, GitHub-ready Salesforce DX project containing the required metadata. Do not replace Salesforce with a generic web application.

PROJECT GOAL
Create a centralized Salesforce-based Farm Management System for farmers, farm managers, buyers, and administrators. The system must manage Farm, Crop, Farmer, and Buyer data, enforce validation, maintain relationships, support role-based access, and provide reports and dashboards.

SOURCE REQUIREMENTS
The supplied document defines:
- Custom objects: Farm, Crop, Farmer, Buyer.
- Salesforce Lightning UI and Salesforce Platform.
- Farm fields including Farm Type, Soil Quality, Irrigation Type, Location, Size, and a Master-Detail relationship with Farmer.
- Crop fields including Crop Name, Planting Date, Harvest Date, Lookup to Farm, Actual Yield, Total Acres Harvested, and Formula field Expected Yield per Acre.
- Farmer fields including Contact Number, State, District, Village, plus State → District dependency.
- Buyer fields including Contact, Email, Address, Buyer Type.
- Farm Management System Lightning App with Farm, Crop, Farmer, Buyer, Reports, and Dashboards.
- Profiles/roles and sharing rules.
- Reports for Farmer/Farm and Crop/Buyer data.
- Dashboard for farm/farmer insights.
- Validation and testing.

IMPLEMENTATION REQUIREMENTS

1. SALESFORCE DX STRUCTURE
Create a valid Salesforce DX repository:
force-app/
  main/
    default/
      objects/
      applications/
      layouts/
      tabs/
      flexipages/
      permissionsets/
      profiles/
      roles/
      sharingRules/
      reports/
      dashboards/
      flows/
      classes/
      triggers/
      customLabels/

Also include:
sfdx-project.json
README.md
.gitignore
LICENSE
manifest/package.xml
docs/
  SETUP.md
  TESTING.md
  DATA_DICTIONARY.md

2. CUSTOM OBJECTS
Create these custom objects:
- Farm__c
- Crop__c
- Farmer__c
- Buyer__c

Use clear labels, plural labels, descriptions, searchable records, reporting enabled, and appropriate page layouts.

3. FARM OBJECT
Create fields:
- Farm_Type__c — Picklist: Crop, Livestock, Mixed
- Soil_Quality__c — Picklist: Organic, Cover Crops, Composting
- Irrigation_Type__c — Picklist: Sprinkler irrigation, Drip irrigation, localized irrigation
- Location__c — Text
- Size__c — Number/Text as appropriate, with sensible validation
- Farmer__c — Master-Detail relationship to Farmer__c

Add useful descriptions/help text. Make required fields where appropriate.

4. CROP OBJECT
Create fields:
- Crop_Name__c — Text
- Planting_Date__c — Date
- Harvest_Date__c — Date
- Farm__c — Lookup relationship to Farm__c
- Actual_Yield__c — Currency/Number as appropriate
- Total_Acres_Harvested__c — Number
- Expected_Yield_per_Acre__c — Formula

Formula:
Expected Yield per Acre = Actual Yield / Total Acres Harvested

Prevent division by zero using a safe Salesforce formula such as:
IF(
  Total_Acres_Harvested__c > 0,
  Actual_Yield__c / Total_Acres_Harvested__c,
  0
)

5. FARMER OBJECT
Create fields:
- Contact_Number__c — Phone
- State__c — Picklist
- District__c — Picklist
- Village__c — Picklist

Implement State → District field dependency. Preserve the source document's stated state examples:
- Telangana
- Andhra Pradesh
- Tamilnadu

Create sensible district mappings and document them clearly. Do not invent unsupported business requirements beyond what is needed to make the dependency functional.

6. BUYER OBJECT
Create:
- Contact__c — Phone
- Email__c — Email
- Address__c — Long Text Area/Text Area
- Buyer_Type__c — Picklist: Wholesale, Retail

7. VALIDATION RULES
Implement useful validation rules consistent with the project:
- Harvest Date cannot be before Planting Date.
- Planting Date should not be after Harvest Date when both exist.
- Total Acres Harvested must be greater than 0 when Actual Yield is entered.
- Actual Yield must not be negative.
- Required business fields must not be blank.
- Farm size must not be negative.
- Email must be valid using Salesforce Email field behavior.
- Contact numbers should be validated only to a reasonable extent; do not create unnecessarily restrictive rules.

Give each validation rule:
- clear name
- user-friendly error message
- error location
- description

8. LIGHTNING APP
Create a Lightning app named:
Farm Management System

Navigation items:
- Home
- Farms
- Crops
- Farmers
- Buyers
- Reports
- Dashboards

Make the app accessible to the intended administrative/managerial users through appropriate permissions.

9. PAGE LAYOUTS / UI
Create usable Lightning page layouts for all four objects.
Display important fields logically.
Include related lists:
- Farm → Crops
- Farmer → Farms
- Buyer-related records if applicable
- Crop → Farm

Do not create unnecessary custom UI components unless they are required.

10. SECURITY
Implement metadata that supports:
- System Administrator full access.
- Farm Manager access to farm, crop, farmer and buyer operational data.
- Sales Department access appropriate to buyer/sales records.
- Object-level and field-level permissions through permission sets or profiles.
- Appropriate sharing model.

Use modern Salesforce security practices where possible. If an older profile configuration from the source document conflicts with current Salesforce best practices, use a permission-set-based approach and document the difference.

11. ROLE
Create/document:
Farm Manager

Place it appropriately in the role hierarchy without inventing a complex organizational hierarchy.

12. SHARING
Implement sharing rules where technically appropriate.
The source project specifically requires:
- Crop records shared with Farm Manager with Read/Write access under the stated criteria.
- Buyer records shared with Sales Department with Read/Write access.

If Salesforce metadata limitations prevent an exact representation of the source wording, implement the closest valid Salesforce configuration and explain it in README.md.

13. AUTOMATION
Create Salesforce Flow automation where appropriate:
- Validate/assist crop data entry.
- Update or process crop-related records when appropriate.
- Provide a notification-ready flow for buyer-related operations if supported without external paid services.

Avoid unnecessary Apex. Prefer Flow, validation rules, formulas, relationships, and standard Salesforce functionality.

14. REPORTS
Create reports including:
A. Farmers with Farms
- Farmer
- Farm
- Farm Type
- Location
- Size

B. Crop Production
- Crop
- Farm
- Planting Date
- Harvest Date
- Actual Yield
- Total Acres Harvested
- Expected Yield per Acre

C. Buyer Transactions / Buyer Overview
- Buyer
- Buyer Type
- Contact
- Email

D. Farm Productivity Summary
- Farm
- Crop
- Yield-related fields
- grouping suitable for management analysis

Use report folders with clear names.

15. DASHBOARD
Create a dashboard named:
Farm Management Dashboard

Include components such as:
- Farmers with Farms
- Crop productivity
- Yield by crop
- Farms by type
- Buyers by type
- Crop/harvest summary

Use standard Salesforce dashboard components and meaningful titles.

16. TESTING
Create a test plan covering:
- Create Farm
- Create Crop
- Create Farmer
- Create Buyer
- Farm/Farmer relationship
- Crop/Farm relationship
- Date validation
- Yield validation
- Formula calculation
- State/District dependency
- Profile/permission behavior
- Sharing rules
- Reports
- Dashboard

If Apex is created, include Apex tests with meaningful assertions and at least the required Salesforce deployment coverage.

17. SAMPLE DATA
Do not hard-code real people's personal information.
Provide a sample-data guide with fictional records:
- 3 Farmers
- 4 Farms
- 5 Crops
- 3 Buyers

Use clearly fictional names and values.

18. DOCUMENTATION
README.md must contain:
- Project title
- Project overview
- Problem statement
- Features
- Salesforce architecture
- Objects and relationships
- Field dictionary
- Validation rules
- Automation
- Security model
- Reports
- Dashboard
- Deployment instructions
- Testing instructions
- Sample data instructions
- Known limitations
- Future scope

Also create:
docs/SETUP.md
docs/TESTING.md
docs/DATA_DICTIONARY.md

19. GITHUB QUALITY
The repository must be clean and professional.
Do NOT include:
- passwords
- Salesforce usernames
- access tokens
- secrets
- personal emails
- node_modules
- unnecessary generated files
- screenshots pretending to be real Salesforce output

Include:
- .gitignore
- LICENSE
- meaningful commit-ready folder structure
- clear README
- package.xml
- sfdx-project.json

20. IMPORTANT ACCURACY RULE
Do not claim that Salesforce configuration has been deployed or tested unless it actually has been verified in a Salesforce org.
If a feature cannot be represented exactly in metadata, document the limitation instead of fabricating it.

21. FINAL OUTPUT REQUIRED
After generating the project:
1. Validate XML/metadata syntax.
2. Check folder structure.
3. Check for missing referenced metadata.
4. Check formulas and field API names for consistency.
5. Check README instructions.
6. Create a ZIP containing the complete Salesforce DX project.
7. Make the ZIP directly uploadable to GitHub as a repository archive.
8. Also provide a concise list of what was implemented and any Salesforce setup steps that still require an actual Salesforce Developer Org.

SUCCESS CRITERIA
The final repository should represent a complete, logically consistent Salesforce Farm Management System based on the supplied requirements, not a generic placeholder project. Every major requirement must either be implemented in metadata or explicitly documented as requiring manual Salesforce setup.
