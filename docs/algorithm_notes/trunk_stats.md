# Trunk Stats Algorithm:


## height above ground
    - max_z - min_z

## Diameter at Breast Height (1.3m up)
    - sample many points at close z range

### Kåsa Circle Fit (Algebraic Least-Squares)

M · [a, b, c]ᵀ = B

Sx   = Σ xᵢ  
Sy   = Σ yᵢ  
Sxx  = Σ xᵢ²  
Syy  = Σ yᵢ²  
Sxy  = Σ xᵢ yᵢ  

Sxxx = Σ xᵢ³  
Syyy = Σ yᵢ³  
Sxxy = Σ xᵢ² yᵢ  
Sxyy = Σ xᵢ yᵢ²  

M =  
[ 2 Sxx   2 Sxy   Sx ]  
[ 2 Sxy   2 Syy   Sy ]  
[  Sx      Sy     n ]

B =  
[ Sxxx + Sxyy ]  
[ Sxxy + Syyy ]  
[ Sxx + Syy   ]

D = 2 * sqrt(a² + b² + c)

## Distance from closest neighbour
