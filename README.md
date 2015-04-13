# ADPM

This directory contains models for AAR distribution prediction, and is intended as a supplement to the paper, "Probabilistic Airport Acceptance Rate Prediction" by Jonathan Cox and Mykel J. Kochenderfer, submitted to the 2016 AIAA Modeling and Simulation Technologies Conference.

Here you will find implementations of the following:
* The Airport Acceptance Rate Distribution Prediction Model (ADPM)
* The Weather Translation Model for Ground Delay Program Planning (WTMG)
* The Baseline model and Models A-D discussed in the above paper

Also included are the trained model parameters for ADPM at San Francisco International and Newark Liberty International airports.

### Get the model
Returns an array whose (i,j,k,m) entry is the probability of AAR m at time t+j given AAR k at time t+j-1 and weather forecast i at time t+j, where i=1 is IMC and i=2 is VMC.

```

$ cd model_parameters
$ julia 
julia> include("readParams.jl")
julia> airport = :SFO
julia> model = readParams(airport)
```

### Layout

```

prediction_models/
    PredictionModels.jl                 Baseline model, models A-D, ADPM
    models.jl                                                    
    weather.jl                          
    normalize.jl                        

wtmg/
    WTMG.jl                             Weather Translation Model for GDP planning
    randomForests.jl
    rfr.py

evaluation/
    CrossValidation.jl                  cross validation module
    scoring.jl                          scoring functions (RMSE, MBS, and RWSE)

model_parameters/
   readParams.jl                        read the model parameters into a Julia array
   adpm_params_sfo                      ADPM model parameters at SFO
   adpm_params_ewr                      ADPM model parameters at EWR
```
