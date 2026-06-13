
=== Run information ===

Scheme:       weka.classifiers.rules.ZeroR 
Relation:     soybean-weka.filters.unsupervised.attribute.Remove-R5-6,8,10,16,20,23,25,27,30,34
Instances:    683
Attributes:   25
              date
              plant-stand
              precip
              temp
              area-damaged
              seed-tmt
              plant-growth
              leaves
              leafspots-halo
              leafspots-marg
              leafspot-size
              leaf-malf
              leaf-mild
              stem
              stem-cankers
              canker-lesion
              external-decay
              int-discolor
              fruit-pods
              fruit-spots
              mold-growth
              seed-discolor
              seed-size
              roots
              class
Test mode:    10-fold cross-validation

=== Classifier model (full training set) ===

ZeroR predicts class value: brown-spot

Time taken to build model: 0 seconds

=== Stratified cross-validation ===
=== Summary ===

Correctly Classified Instances          92               13.47   %
Incorrectly Classified Instances       591               86.53   %
Kappa statistic                          0     
Mean absolute error                      0.0961
Root mean squared error                  0.2191
Relative absolute error                100      %
Root relative squared error            100      %
Total Number of Instances              683     

=== Detailed Accuracy By Class ===

 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
0.000    0.000    ?          0.000    ?          ?        0.498     0.029     diaporthe-stem-canker
0.000    0.000    ?          0.000    ?          ?        0.498     0.029     charcoal-rot
0.000    0.000    ?          0.000    ?          ?        0.498     0.029     rhizoctonia-root-rot
0.000    0.000    ?          0.000    ?          ?        0.489     0.126     phytophthora-rot
0.000    0.000    ?          0.000    ?          ?        0.469     0.061     brown-stem-rot
0.000    0.000    ?          0.000    ?          ?        0.498     0.029     powdery-mildew
0.000    0.000    ?          0.000    ?          ?        0.498     0.029     downy-mildew
1.000    1.000    0.135    1.000    0.237      ?        0.488     0.132     brown-spot
0.000    0.000    ?          0.000    ?          ?        0.498     0.029     bacterial-blight
0.000    0.000    ?          0.000    ?          ?        0.498     0.029     bacterial-pustule
0.000    0.000    ?          0.000    ?          ?        0.498     0.029     purple-seed-stain
 0.000    0.000    ?          0.000    ?          ?        0.469     0.061     anthracnose
0.000    0.000    ?          0.000    ?          ?        0.498     0.029     phyllosticta-leaf-spot
0.000    0.000    ?          0.000    ?          ?        0.493     0.131     alternarialeaf-spot
0.000    0.000    ?          0.000    ?          ?        0.494     0.132     frog-eye-leaf-spot
0.000    0.000    ?          0.000    ?          ?        0.415     0.019     diaporthe-pod-&-stem-blight
0.000    0.000    ?          0.000    ?          ?        0.412     0.017     cyst-nematode
0.000    0.000    ?          0.000    ?          ?        0.423     0.020     2-4-d-injury
0.000    0.000    ?          0.000    ?          ?        0.398     0.011     herbicide-injury
0.135    0.135    ?          0.135    ?          ?        0.484     0.086     Weighted Avg.  

=== Confusion Matrix ===

  a  b  c  d  e  f  g  h  i  j  k  l  m  n  o  p  q  r  s   <-- classified as
  0  0  0  0  0  0  0 20  0  0  0  0  0  0  0  0  0  0  0 |  a = diaporthe-stem-canker
  0  0  0  0  0  0  0 20  0  0  0  0  0  0  0  0  0  0  0 |  b = charcoal-rot
  0  0  0  0  0  0  0 20  0  0  0  0  0  0  0  0  0  0  0 |  c = rhizoctonia-root-rot
  0  0  0  0  0  0  0 88  0  0  0  0  0  0  0  0  0  0  0 |  d = phytophthora-rot
  0  0  0  0  0  0  0 44  0  0  0  0  0  0  0  0  0  0  0 |  e = brown-stem-rot
  0  0  0  0  0  0  0 20  0  0  0  0  0  0  0  0  0  0  0 |  f = powdery-mildew
  0  0  0  0  0  0  0 20  0  0  0  0  0  0  0  0  0  0  0 |  g = downy-mildew
  0  0  0  0  0  0  0 92  0  0  0  0  0  0  0  0  0  0  0 |  h = brown-spot
  0  0  0  0  0  0  0 20  0  0  0  0  0  0  0  0  0  0  0 |  i = bacterial-blight
  0  0  0  0  0  0  0 20  0  0  0  0  0  0  0  0  0  0  0 |  j = bacterial-pustule
  0  0  0  0  0  0  0 20  0  0  0  0  0  0  0  0  0  0  0 |  k = purple-seed-stain
  0  0  0  0  0  0  0 44  0  0  0  0  0  0  0  0  0  0  0 |  l = anthracnose
  0  0  0  0  0  0  0 20  0  0  0  0  0  0  0  0  0  0  0 |  m = phyllosticta-leaf-spot
  0  0  0  0  0  0  0 91  0  0  0  0  0  0  0  0  0  0  0 |  n = alternarialeaf-spot
  0  0  0  0  0  0  0 91  0  0  0  0  0  0  0  0  0  0  0 |  o = frog-eye-leaf-spot
  0  0  0  0  0  0  0 15  0  0  0  0  0  0  0  0  0  0  0 |  p = diaporthe-pod-&-stem-blight
  0  0  0  0  0  0  0 14  0  0  0  0  0  0  0  0  0  0  0 |  q = cyst-nematode
  0  0  0  0  0  0  0 16  0  0  0  0  0  0  0  0  0  0  0 |  r = 2-4-d-injury
  0  0  0  0  0  0  0  8  0  0  0  0  0  0  0  0  0  0  0 |  s = herbicide-injury





