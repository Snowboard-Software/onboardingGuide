# ❄️🏂  Snowboard Guide to building trust in your Snowflake Data 🏂❄️

❄️🏂 In order to enable a data mesh and s better self-service of analytics, data teams should treat the data they collect as assets and the data they produce as products for each analytical use case (marketing, finance, product etc). In order to make these products consumable by any relevant 3rd party in the organization, these assets need to be well documented by their owners. 

The goal of Snowboard is to become the **repository of all the data knowledge** of your organization. This knowledge is particularly useful to facilitate collaboration between data engineers, data analysts and business stakeholders who consume data. 🏂❄️

🏋️‍♂️ Investing time in setting up proper documentation processes will pay-off for the data team ten folds: 

a) Make your company decision makers more confident with data.

b) Helping your stakeholders understand their dashboards, operations and data.

c) Save time aligning everyone on definition and metrics. 

d) Onboard new joiners faster and save the knowledge of your experienced data wizards!

As a general rule we will follow a simple principle, when it comes to documentation we will start with stakeholders facing documentation as the goal is to give context for data consumers and we move upstream toward raw data.

📚 **GLOSSARY:**

**I. PERMISSIONS AND SET-UP**

1. Grant permissions
2. Run background jobs

**II. DOCUMENTATION FOR CATALOGUE**

**A. GET STARTED** 

1. Identify use case
2. Create tags and properties
3. Document business terms
4. Document workbook and dashboard
5. Document reporting tables
6. Document databases and schemas

**B. ITERATE OVER MORE USE CASES**

**III. OTHER TRUST FEATURES**

1. Data lineage 
2. Data freshness

**IV. DEFINE METRICS**

**A. GET STARTED**

1. Identify use case
2. Model metric
3. Consume metrics

**B. ITERATE OVER MORE USE CASES**

**V. QUESTIONS, FEEDBACK ON BUGS AND USABILITY**

**END**

## HOW TO START

## 🛠 I. PERMISSIONS AND SET-UP

1. **Grant Snowflake permissions** to Snowboard technical user.
2. **Run background jobs** (in settings top right corner of the app, click on your name initial) for indexing existing assets (DBs, schemas, tables, columns in Snowflake) and extracting metadata (usage, freshness, size, lineage). [This can take up to 1 day depending on the size of the installation]

![Scheduling background jobs.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/Scheduling_background_jobs.png)

**Outcome:** Congratulations your assets are now indexed and discoverable in Snowboard!

## 🧙 II. DOCUMENTATION FOR CATALOGUE

### A. GET STARTED

1. **Identify use case.** Recommendation: for the first one chose an analytics use case critical for the organization (e.g. acquisition funnel for a B2C start-up). **GOAL:** build a target picture of who will benefit from documentation and what assets needs to be documented.
    1. Who are the stakeholders? (data producers and consumers: BI analysts responsible for e.g. marketing, marketing managers, marketing operation specialists)
    2. What are the dashboards? (e.g. marketing performance dashboards in Tableau or PowerBI for example)
    3. What are the concepts and definitions to document for people not familiar with the use case? (e.g. defining the stages of your funnel and what each conversion concretely means would help someone consuming dashboards)
    4. What are the underlying reporting tables on top of which dashboards should be built?

1. **Create Tags and Properties.** Here this depend a lot of your particular needs and documentation strategy but we recommend to use tags for lifecycle management of assets (asset: “approved”, “wip”, “deprecated”), critical information (”PII data” or “issue detected”), documentation steps (”to be documented”) and if you have domains exclusive to each other. (e.g. we have data coming from many disparate sources, data for “snowboard”, demo data of a ramen dealer shop “ramen”). 
    
    ![create tags and properties.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/create_tags_and_properties.png)
    

1. **Document business terms definition.** Create 3 important business terms. (see 1. d.)
    
    
    ![business terms.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/business_terms.png)
    
2. **Document one workbook and the dashboards** within (related to use case). ****Document what analytical questions does this dashboard answer, and use #hashtags to reference business terms defined previously.
    
    
    ![tableau dashboarsd documentation.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/tableau_dashboarsd_documentation.png)
    
3. **Document reporting tables** underneath use case Tableau or PowerBI dashboards. If you want to enable good self service, these are the most important tables to document first. Data consumers need to understand what is the definition of each columns. The next natural step here is to select a table where complex business logic has been applied and document the result variables. 

![document reporting table.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/document_reporting_table.png)

 

1. **Document the database and schemas** (related to use case) with at least 1 sentence describing the type of data that can be found and the purpose of the object (e.g. database: “contains data related to e-commerce shop”.) and who is the owner.
    
    
    ![document schema.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/document_schema.png)
    
    **Outcome:** Congratulations you have identified an analytical use case and documented it! 
    

### B. ITERATE OVER MORE USE CASES

## 🛡III. OTHER TRUST FEATURES

1. **Explore data with table level lineage.** 
    1. Where is the data coming from? Start on the workbook page of your BI tool. Go down to lineage. Press “Up +” button to see all tables upstream. Click on a table to jump to its catalogue page.  
        
        ![upstream dependency of table.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/upstream_dependency_of_table.png)
        
    2. Where is this column coming from? Start on a table catalog page, take a variable in the list, click on the node icon next to a variable “completeness” and “monthly usage”. You have the column level lineage. 
        
        ![click on node edge symbol next to variable to assess column level lineage.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/click_on_node_edge_symbol_next_to_variable_to_assess_column_level_lineage.png)
        
    3. Which dashboard is built on this data? If I change this table which dashboard is impacted? Start from the catalog page of a table. Go to lineage. Click “Down -” to see all the downstream dependencies of a particular table. Click on a table to jump to its catalogue page. 
        
        ![downstream dependency of tables.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/downstream_dependency_of_tables.png)
        
    4. How was this particular table on the lineage created? Hover an arrow between two tables and click on it. Here you have the sql that defined this table. 
        
        ![click on arrow for sql statement behind creation of table.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/click_on_arrow_for_sql_statement_behind_creation_of_table.png)
        
2. **Assess freshness of tables**
    1. Are there tables in my schema that are not fresh? Go to schema catalogue page. Sort tables by DESC last updated. Is there anything unusual? 
        
        ![sort tables in schema by desc last updated.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/sort_tables_in_schema_by_desc_last_updated.png)
        
    2. When was a table last used, when was it last updated? Go a to a table catalog page. Go down to timeline. There are two toggles: “updated”, “used”.
        
        ![timeline upadet and usage.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/timeline_upadet_and_usage.png)
        

## 👨‍🚀 IV. DEFINE METRICS

1. **Identify use case.** We recommend to start with a simple metric like revenue. 
    1. Who consume revenue as a metric? 
    2. What does revenue mean exactly?
    3. Which system gives the data for revenue?
    4. What table should revenue be built upon?
    5. What time dimension do you want revenue to be calculated over?
    6. What other dimensions to you want to be able to slice and dice revenue with? 
    7. What is the sql formula for revenue metric? 
2. **Model a metric.** Click on new metric on the top right corner. Fill above information.

![define metric.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/define_metric.png)

1. **Consume metrics from the store.**
    
    ![metric store consumption.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/metric_store_consumption.png)
    

1. **Consume metrics from Snowflake.**
2. **Consume metrics from Tableau/PowerBI.** 

## V. GIVE FEEDBACK TO THE SNOWBOARD TEAM FOR FEATURE REQUEST, QUESTIONS AND BUGS

Click the blue “feedback” button at the down right corner of your screen. You can take screenshots to point towards what is wrong.

![give feedback to the snowboard team.png](https://github.com/Snowboard-Software/onboardingGuide/raw/master/img/give_feedback_to_the_snowboard_team.png)

# 🎉🎉   CONGRATULATIONS! THIS IS THE END OF YOUR ONBOARDING!  🎉🎉