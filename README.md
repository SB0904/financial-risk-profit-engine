Project Title: Financial Risk & Profit Optimization Engine

The Challenge In commercial lending, the cost of being wrong is not equal. A Default (False Negative) costs a bank ~$150k in principal, while a Rejection (False Positive) only costs ~$15k in lost interest. Standard Machine Learning models optimize for "Accuracy," treating these unequal errors identically. I aimed to build a system that optimized for Net Profit, prioritizing financial health over statistical precision.

The Solution: I engineered a risk decision engine using XGBoost on 800,000+ SBA loans, implementing three key innovations:

Profit Maximization: I developed a custom cost function that weighs defaults 12x heavier than lost opportunities. By simulating P&L, I identified that the standard probability threshold (0.50) was financially inefficient.

Time-Series Validation: To prevent "Data Leakage," I sorted data by DisbursementDate before splitting. This ensured the model was trained only on past data to predict future performance—a critical requirement in FinTech.

Explainability: I integrated SHAP values to allow stakeholders to view the specific "why" behind every loan rejection, ensuring regulatory transparency.

Development Methodology: I independently researched SBA loan patterns and architected the core profit-maximization logic in Python. Once the prototype was functional, I utilized AI tools to refactor the codebase for modularity and optimize runtime performance, simulating a real-world software engineering workflow where modern tools are used to enhance human-led design.

The Result By recalibrating the decision threshold to 0.62, the model projected a $20M increase in net profit on the test set compared to baseline logic, significantly reducing risk exposure while maintaining profitable volume.
