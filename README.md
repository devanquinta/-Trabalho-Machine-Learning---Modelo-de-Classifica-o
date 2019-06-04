# -Trabalho-Machine-Learning---Modelo-de-Classifica-o
#########
#########
de  sklearn.datasets  import  load_breast_cancer
cancer  =  load_breast_cancer ()
de impressão ( "cancer.keys (): \ n {} " . formato ( câncer . chaves ()))
cancer.keys (): 
dict_keys (['DESCR', 'target_names', 'feature_names', 'alvo', 'dados'])
#primera parte do trabalho
X  =  câncer . dados 
y  =  câncer . alvo
# Modelo inteiro de trem Acurácia: KNN (1), KNN (5) e LogReg
#logReg
de  sklearn.linear_model  import  LogisticRegression
logreg  =  LogisticRegression ()
# logReg 
de  sklearn  import  métricas 
print ( métricas . accuracy_score ( y ,  y_pred ))
0,9595782073813708
# KNN (K = 5)
de  sklearn.neighbors  importar  KNeighborsClassifier 
knn  =  KNeighborsClassifier ( n_neighbors = 5 ) 
knn . ajuste ( X ,  y ) 
y_pred  =  knn . prever ( X ) 
impressão ( métricas . accuracy_score ( y ,  y_pred ))
0,9472759226713533
# KNN (K = 1) # 100% não é o ideal
knn  =  KNeighborsClassifier ( n_neighbors = 1 ) 
knn . ajuste ( X ,  y ) 
y_pred  =  knn . prever ( X ) 
impressão ( métricas . accuracy_score ( y ,  y_pred ))
1,0
# Comboio Acurácia / Split de Teste: KNN (1), KNN (5) e LogReg
#logReg
de  sklearn.model_selection  import  train_test_split 
X_train ,  X_test ,  y_train ,  y_test  =  train_test_split ( X ,  y ,  test_size = 0,4 ,  random_state = 4 )
y_pred  =  logreg . predict ( X_test )
print ( métricas . accuracy_score ( y_test ,  y_pred ))
0,9517543859649122
# Repita para KNN com K = 5 # - fraco
knn  =  KNeighborsClassifier ( n_neighbors = 5 ) 
knn . ajuste ( X_train ,  y_train ) 
y_pred  =  knn . prever ( X_test ) 
print ( métricas . accuracy_score ( y_test ,  y_pred ))
0,9078947368421053
# Repetir para KNN com K = 1 
knn  =  KNeighborsClassifier ( n_neighbors = 1 ) 
knn . ajuste ( X_train ,  y_train ) 
y_pred  =  knn . prever ( X_test ) 
print ( métricas . accuracy_score ( y_test ,  y_pred ))
0,9035087719298246
# Gráfico de Tunning KNN (1-25)
# tente K = 1 até K = 25 e registre a precisão do teste 
k_range  =  list ( range ( 1 ,  26 )) 
scores  =  [] 
para  k  em  k_range : 
    knn  =  KNeighborsClassifier ( n_neighbors = k ) 
    knn . ajuste ( X_train ,  y_train ) 
    y_pred  =  knn . prever pontuações ( X_test ) 
    . acrescentar ( métricas .accuracy_score ( y_test ,  y_pred ))
# import Matplotlib (biblioteca de plotagem científica) 
import  matplotlib.pyplot  as  plt

# permite que gráficos apareçam dentro do notebook 
% matplotlib inline

# traçar o relacionamento entre K e testar a precisão 
plt . enredo ( k_range ,  escores ) 
plt . xlabel ( 'Valor de K para KNN' ) 
plt . ylabel ( 'Exatidão de teste' )
Texto (0,0,5, 'Exatidão de teste')

# instanciar o modelo com os parâmetros mais conhecidos 
knn  =  KNeighborsClassifier ( n_neighbors = 8 )
knn . ajuste ( X ,  y )
KNeighborsClassifier (algoritmo = 'auto', leaf_size = 30, métrica = 'minkowski',
           metric_params = Nenhum, n_jobs = 1, n_neighbors = 8, p = 2,
           pesos = 'uniforme')
y_pred  =  knn . prever ( X ) 
impressão ( métricas . accuracy_score ( y ,  y_pred ))
0,9384885764499121
#############################################################################################33
# Qual o melhor modelo com melhor acurácia?
# Gráfico de Tunning KNN (8) 
