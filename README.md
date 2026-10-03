from pyspark.sql import SparkSession
from pyspark.sql.functions import col, desc, asc, when

spark = SparkSession.builder\
  .appName("Gestao_De_Cidade")\
  .getOrCreate()

# Tabela A:Cidadãos (ID, Nome, Idade, Bairro_ID)
dados_cidadaos = [
    (1,"Ana Silva",28,10),
    (2,"João Bento",45,10),
    (3,"Maria Luz",19,20),
    (4,"Carlos Vaz",35,30),
    (5,"Sofia Rosa",22,20)
]

# Tabela B:Consumo de Energia por Bairro (Bairro_ID, Nome_Bairro, Consumo_KWh)
dados_bairros = [
    (10,"Centro Histórico",5000),
    (20,"Zona Ribeirinha",3500),
    (30,"Parque Das Nações",7000),
    (40,"Bairro Alto",2000)
]

cidadaos = spark.createDataFrame(dados_cidadaos, ["ID", "Nome", "Idade", "Bairro_ID"])
bairros = spark.createDataFrame(dados_bairros, ["Bairro_ID", "NomeBairro", "ConsumoEnergia"])

print("Registros;")
cidadaos.show()
bairros.show()
