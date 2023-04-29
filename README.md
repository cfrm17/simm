# An Overview of Standard Initial Margin Model

Initial Margin (IM) is the amount of collateral required to open a position with a broker or an exchange or a bank. The Standard Initial Margin Model (SIMM) is very likely to become the market standard. It is designed to provide a common methodology for calculating initial margin for uncleared OTC derivatives. Initial margin calculation is counterparty-portfolio-based. Given this standardized approach, counterparties can easily reconcile the results. 

Initial margin calculation is counterparty-portfolio-based. It applies to non-cleared OTC derivatives only. Derivative trades belonging to a counterparty will be divided into cleared-trade portfolio and non-cleared-trade portfolio. The initial margin is computed for the non-cleared portfolio. This presentation provides many practical details of the SIMM. 

Keywords
Margin, initial margin, standard initial margin model, collateral

	Margin Introduction
	Margin is collateral that one party needs to deposit with a broker or an exchange to cover some or all of the credit risk.
	Initial Margin: it is the amount of collateral required to open a position.
	Maintenance Margin: it is the minimum amount of collateral required to keep the position open after inception.
	Margin Balance = Asset value – Borrowed fund
	Margin Call: if (Margin balance) < (Maintenance margin), the broker issues a margin call that requires the investor to bring the margin balance back to initial margin.

	Initial Margin Scope
	Initial margin calculation is counterparty-portfolio-based.
	Calculation is for non-cleared OTC derivatives only.
	Derivative trades belonging to a counterparty will be divided into cleared-trade portfolio and non-cleared-trade portfolio. The initial margin is computed for the non-cleared portfolio.

	Initial Margin Calculation hierarchy
	Calculation is conducted from the lowest level to the highest: risk factor –> risk bucket risk measure  risk class  product class  final initial margin
	Define 4 product classes
	Interest Rates and Foreign Exchange (RatesFX)
	Credit
	Equity
	Commodity
	Define 6 risk classes
	Interest Rate
	Credit (Qualifying): non-securitization and simple securitization
	Credit (Non-Qualifying): complex securitization
	Equity
	Commodity
	FX
	Define 3 risk measures
	Delta
	Vega
	Curvature
	Define risk buckets
	Interest rate bucket: based on currency (USD, EUR, CAD, …)
	Credit bucket: based on credit quality (sovereign, financial, technology, …)
	Equity bucket: based on sector (financial, industrial, …)
	Commodity bucket: based on commodity type (crude, gas, …)
	FX: each FX rate is a bucket
	Define risk factors
	Interest rate curve: 12 yields
	Credit curve: 5 spreads
	Equity: spot price
	Commodity: spot price
	FX: exchange rate

	Sensitivity Calculation
	Delta

	Interest rate (PV01): 	s(i,r_t )=V_i (r_t+1bp,〖cs〗_i )-V_i (r_t,〖cs〗_t)
where r_t – interest rate; 〖cs〗_t – credit spread; 1bp – 1 basis point; V_i – market value
	Credit (CS01): 	s(i,〖cs〗_t )=V_i (r_(t,),〖cs〗_i+1bp)-V_i (r_t,〖cs〗_t)
	Equity:	s_ik=V_i (〖EQ〗_k+1%〖EQ〗_k )-V_i (〖EQ〗_k)
where 〖EQ〗_k – spot price of equity k.
	Commodity:	s_ik=V_i (〖CTY〗_k+1%〖CTY〗_k )-V_i (〖CTY〗_k)
where 〖CTY〗_k – spot price of commodity k.
	FX:	s_ik=V_i (〖FX〗_k+1%〖FX〗_k )-V_i (〖FX〗_k)
where 〖FX〗_k – spot exchange rate of base currency k.

	Vega

  〖VR〗_ik=∑_j▒〖σ_kj  〖dV〗_i/dσ〗
  where σ_ik – implied volatility


	Curvature

 
 where  is a scaling factor and t_kj is the expiry date.

	Initial Margin Calculation
	A risk weight is defined for each risk factor.
	A correlation is specified for each risk factor pair.
	Within a product class, calculate initial margin for each risk class
	Net all sensitivities for each risk factor k to get the summed  s_k
	Compute risk weighted sensitivity  
where 〖WS〗_k – risk weight and 〖CR〗_k – concentration risk factor
	Aggregate weighted sensitivities within each bucket
 
where ρ_ki – correlation and f_ki – correlation adjustment
	Aggregate buckets to obtain sensitivity initial margin
DeltaMargin=√(∑_b▒K_b^2 +∑_b▒∑_(b≠c)▒〖γ_bc S_b S_c 〗)+K_residual
 
VegaMargin=√(∑_b▒K_b^2 +∑_b▒∑_(b≠c)▒〖γ_bc 〖δ_bc S〗_b S_c 〗)+K_residual
 

CurvatureMargin=max(∑_(b,k)▒〖CVR〗_(b,k) +λ√(∑_b▒K_b^2 +∑_b▒∑_(b≠c)▒〖γ_bc^2 S_b S_c 〗))+θ_residual
 
where  γ_bc – correlation between bucket b and c
	K_residual – K value for residual bucket
	Initial margin for a risk class
〖IM〗_x=〖DeltaMargin〗_x+〖VegaMargin〗_x+〖CurvatureMargin〗_x
	Initial margin for the product class
 


	Final total initial margin

 



IM=〖IM〗_RateFX+〖IM〗_Credit+〖IM〗_Equity+〖IM〗_Commodity
 

〖IM〗_p=√(∑_r▒〖IM〗_r^2 +∑_r▒∑_(s≠r)▒〖Ψ_rs 〖IM〗_r 〖IM〗_s 〗)


References:

https://finpricing.com/lib/IrCurveIntroduction.html
