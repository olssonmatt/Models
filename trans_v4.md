# Trans v4 Model Rebuild

---

## Background
   - Score that detects delinquency from transaction data

---

## Notes from Trans v3; Documentation
   - Possible reading;
      - Early Identification of High Risk Credit Card Customers Based on Behavourial Data
      - SMOTE Paper
      - FICO Falcon Fraud Manager (still used? fraud accounts to be removed?)
   - Considerations;
      - New SKUs
      - New variable functions as derivative > Ratios, or time based ratios
      - Development, validation data time periods
   - Tables used;
      - trans/vw_trans
      - trans_cat_code_lu
      - sku_data
      - authlog
   - Score Definition; 700 has 30:1 odds; PDO 30
      - one of every 30 accounts is bad at 700
      - at 730 those odds change to 60:1
      - at 760 they change to 120:1
      - Bad Definition; (PD4+ or PD3 at month 12) and charge-off/bankruptcy within 12 months
   - Good Definition; At most PD1 within 12 months or at most PD2 within 12 months and PD0 on 12th month
   - Exclusions; Test accounts, bankrupt at obs, c/o at obs, deceased at obs, fraud at obs, closed & 0 bal at obs, revoked & 0 bal at obs, not retail cards, < 2 purchases in 12 months, <$100 purchases in 12 months
   - Model Exclusions; expense accts, employees, bill cycle change at current (reages?), VIPs, deceased, lost/stolen, fraud
   - Indeterminates
      - max PD3 and final PD in (0,1,2)
      - max PD2 and final PD in (1,2)
   - Trans v3 Project Plan
      - preliminary analysis includes re-creating variables in previous scorecard
      - brainstorming on new variables and code
      - developing data dictionary
      - perform correlation and WOE analysis to select variables going into EM (enterprise miner)
      - create and finalize segmentation scheme
      - build model/scorecard
      - perform internal and external validations
      - impact analyses
      - create scoring code, coordinate with IT, or implemention team on execution process
      - orgainze project documentation and update CMOD summary documentation
      - develop tracking reports

## Notes from Trans v3; Preliminary Analysis
   - Bad definition goes through iterations and analysis
   - Falcon score testing, not too sure if used in final build or available today
      - Bad rate by falcon scoring
   - Looks at sku data and missing sku data from in house sources (Marks, Sportchek, CT, etc.)
   - Performance analysis looks at performance of bad rates?
   - Production exclusions; 
      - accounts with <2 transactions in the last 12 months
         - 1 transaction is volatile and bad rate considerations
      - <$60 spent in the last 12 months 
         - bad rate considerationsS


## Notes from Trans v3; Study Files
