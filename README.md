# Data Analysis Portfolio

# Projects
-  EDA on Cyclistic Data
   Developed EDA for Clyclist data from 2023 using Python to make Data-driven decisions on bussines. 
  


[Uploading Cyclist.{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Cyclistic Proyecto "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Eres un analista de datos júnior que trabaja en el equipo de analistas de marketing de Cyclistic, una empresa de bicicletas compartidas de Chicago. La directora de marketing cree que el éxito futuro de la empresa depende de maximizar la cantidad de membresías anuales. Por lo tanto, tu equipo quiere entender qué diferencias existen en el uso de las bicicletas Cyclistic entre los ciclistas ocasionales y los miembros anuales. A través de estos conocimientos, tu equipo diseñará una nueva estrategia de marketing para convertir a los ciclistas ocasionales en miembros anuales. Sin embargo, antes de eso, los ejecutivos de Cyclistic deben aprobar tus recomendaciones; por eso, debes respaldar tu propuesta con una visión convincente de los datos y visualizaciones profesionales de los mismos.\n",
    "\n",
    "\n",
    "Hasta ahora, la estrategia de marketing de Cyclistic se basaba en la construcción de un reconocimiento de marca general y en atraer a amplios segmentos de consumidores. Uno de los enfoques que ayudó a hacer esto posible fue la flexibilidad de sus planes de precios: pases de un solo viaje, pases de un día completo y membresías anuales. A los clientes que compran pases de un solo viaje o pases de un día completo se los llama ciclistas ocasionales. Los clientes que compran membresías anuales se llaman miembros de Cyclistic.\n",
    "\n",
    "\n",
    "El equipo de Marketing estableció una meta clara: Diseñar estrategias de marketing orientadas a convertir a los ciclistas ocasionales en miembros anuales. Sin embargo, para hacer eso, el equipo de analistas de marketing necesita entender mejor cómo difieren los miembros anuales y los ciclistas ocasionales, por qué los ciclistas ocasionales comprarían una membresía y cómo los medios digitales podrían afectar sus tácticas de marketing. El equipo están interesados en analizar los datos históricos de viajes en bicicleta de Cyclistic para identificar tendencias.\n",
    "\n",
    "El Jefe de marketing te asigno la siguiente pregunta: ¿En qué se diferencian los socios anuales y los ciclistas ocasionales con respecto al uso de las bicicletas de Cyclistic?"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Lectura de Datos"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Vamos a importar las librerias que utilizaremos"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "import pandas as pd #data frames\n",
    "import numpy as np  #funciones numericas\n",
    "import matplotlib.pyplot as plt #graficar\n",
    "import seaborn as sns\n",
    "import mplfinance as mpf"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Vamos a asignar una variable a cada data frame"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [],
   "source": [
    "df1=pd.read_csv('Trip_Q1.csv')\n",
    "df2=pd.read_csv('Trip_Q2.csv')\n",
    "df3=pd.read_csv('Trip_Q3.csv')\n",
    "df4=pd.read_csv('Trip_Q4.csv')\n",
    "df5=pd.read_csv('Trip_Q5.csv')\n",
    "df6=pd.read_csv('Trip_Q6.csv')\n",
    "df7=pd.read_csv('Trip_Q7.csv')\n",
    "df8=pd.read_csv('Trip_Q8.csv')\n",
    "df9=pd.read_csv('Trip_Q9.csv')\n",
    "df10=pd.read_csv('Trip_Q10.csv')\n",
    "df11=pd.read_csv('Trip_Q11.csv')\n",
    "df12=pd.read_csv('Trip_Q12.csv')\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Exploracion de Datos "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Queremos ver la informacion relevante, que variables y tipo de datos contiene "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 85,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 181806 entries, 0 to 181805\n",
      "Data columns (total 15 columns):\n",
      " #   Column              Non-Null Count   Dtype          \n",
      "---  ------              --------------   -----          \n",
      " 0   ride_id             181806 non-null  object         \n",
      " 1   rideable_type       181806 non-null  object         \n",
      " 2   started_at          181806 non-null  datetime64[ns] \n",
      " 3   ended_at            181806 non-null  datetime64[ns] \n",
      " 4   start_station_name  152523 non-null  object         \n",
      " 5   start_station_id    152523 non-null  object         \n",
      " 6   end_station_name    150648 non-null  object         \n",
      " 7   end_station_id      150648 non-null  object         \n",
      " 8   start_lat           181806 non-null  float64        \n",
      " 9   start_lng           181806 non-null  float64        \n",
      " 10  end_lat             181678 non-null  float64        \n",
      " 11  end_lng             181678 non-null  float64        \n",
      " 12  member_casual       181806 non-null  object         \n",
      " 13  ride_time           181806 non-null  timedelta64[ns]\n",
      " 14  weekday             181806 non-null  object         \n",
      "dtypes: datetime64[ns](2), float64(4), object(8), timedelta64[ns](1)\n",
      "memory usage: 20.8+ MB\n"
     ]
    }
   ],
   "source": [
    "df1.info()\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Vizualizamos las primeras lineas del Data Frame "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 65,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>ride_id</th>\n",
       "      <th>rideable_type</th>\n",
       "      <th>started_at</th>\n",
       "      <th>ended_at</th>\n",
       "      <th>start_station_name</th>\n",
       "      <th>start_station_id</th>\n",
       "      <th>end_station_name</th>\n",
       "      <th>end_station_id</th>\n",
       "      <th>start_lat</th>\n",
       "      <th>start_lng</th>\n",
       "      <th>end_lat</th>\n",
       "      <th>end_lng</th>\n",
       "      <th>member_casual</th>\n",
       "      <th>ride_time</th>\n",
       "      <th>weekday</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>65DBD2F447EC51C2</td>\n",
       "      <td>electric_bike</td>\n",
       "      <td>2022-12-05 10:47:18</td>\n",
       "      <td>2022-12-05 10:56:34</td>\n",
       "      <td>Clifton Ave &amp; Armitage Ave</td>\n",
       "      <td>TA1307000163</td>\n",
       "      <td>Sedgwick St &amp; Webster Ave</td>\n",
       "      <td>13191</td>\n",
       "      <td>41.918244</td>\n",
       "      <td>-87.657115</td>\n",
       "      <td>41.922167</td>\n",
       "      <td>-87.638888</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:09:16</td>\n",
       "      <td>Monday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>0C201AA7EA0EA1AD</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2022-12-18 06:42:33</td>\n",
       "      <td>2022-12-18 07:08:44</td>\n",
       "      <td>Broadway &amp; Belmont Ave</td>\n",
       "      <td>13277</td>\n",
       "      <td>Sedgwick St &amp; Webster Ave</td>\n",
       "      <td>13191</td>\n",
       "      <td>41.940106</td>\n",
       "      <td>-87.645451</td>\n",
       "      <td>41.922167</td>\n",
       "      <td>-87.638888</td>\n",
       "      <td>casual</td>\n",
       "      <td>0 days 00:26:11</td>\n",
       "      <td>Sunday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>E0B148CCB358A49D</td>\n",
       "      <td>electric_bike</td>\n",
       "      <td>2022-12-13 08:47:45</td>\n",
       "      <td>2022-12-13 08:59:51</td>\n",
       "      <td>Sangamon St &amp; Lake St</td>\n",
       "      <td>TA1306000015</td>\n",
       "      <td>St. Clair St &amp; Erie St</td>\n",
       "      <td>13016</td>\n",
       "      <td>41.885919</td>\n",
       "      <td>-87.651133</td>\n",
       "      <td>41.894345</td>\n",
       "      <td>-87.622798</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:12:06</td>\n",
       "      <td>Tuesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>54C5775D2B7C9188</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2022-12-13 18:50:47</td>\n",
       "      <td>2022-12-13 19:19:48</td>\n",
       "      <td>Shields Ave &amp; 31st St</td>\n",
       "      <td>KA1503000038</td>\n",
       "      <td>Damen Ave &amp; Madison St</td>\n",
       "      <td>13134</td>\n",
       "      <td>41.838464</td>\n",
       "      <td>-87.635406</td>\n",
       "      <td>41.881370</td>\n",
       "      <td>-87.674930</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:29:01</td>\n",
       "      <td>Tuesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>A4891F78776D35DF</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2022-12-14 16:13:39</td>\n",
       "      <td>2022-12-14 16:27:50</td>\n",
       "      <td>Ashland Ave &amp; Chicago Ave</td>\n",
       "      <td>13247</td>\n",
       "      <td>Damen Ave &amp; Charleston St</td>\n",
       "      <td>13288</td>\n",
       "      <td>41.895954</td>\n",
       "      <td>-87.667728</td>\n",
       "      <td>41.920082</td>\n",
       "      <td>-87.677855</td>\n",
       "      <td>casual</td>\n",
       "      <td>0 days 00:14:11</td>\n",
       "      <td>Wednesday</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            ride_id  rideable_type          started_at            ended_at  \\\n",
       "0  65DBD2F447EC51C2  electric_bike 2022-12-05 10:47:18 2022-12-05 10:56:34   \n",
       "1  0C201AA7EA0EA1AD   classic_bike 2022-12-18 06:42:33 2022-12-18 07:08:44   \n",
       "2  E0B148CCB358A49D  electric_bike 2022-12-13 08:47:45 2022-12-13 08:59:51   \n",
       "3  54C5775D2B7C9188   classic_bike 2022-12-13 18:50:47 2022-12-13 19:19:48   \n",
       "4  A4891F78776D35DF   classic_bike 2022-12-14 16:13:39 2022-12-14 16:27:50   \n",
       "\n",
       "           start_station_name start_station_id           end_station_name  \\\n",
       "0  Clifton Ave & Armitage Ave     TA1307000163  Sedgwick St & Webster Ave   \n",
       "1      Broadway & Belmont Ave            13277  Sedgwick St & Webster Ave   \n",
       "2       Sangamon St & Lake St     TA1306000015     St. Clair St & Erie St   \n",
       "3       Shields Ave & 31st St     KA1503000038     Damen Ave & Madison St   \n",
       "4   Ashland Ave & Chicago Ave            13247  Damen Ave & Charleston St   \n",
       "\n",
       "  end_station_id  start_lat  start_lng    end_lat    end_lng member_casual  \\\n",
       "0          13191  41.918244 -87.657115  41.922167 -87.638888        member   \n",
       "1          13191  41.940106 -87.645451  41.922167 -87.638888        casual   \n",
       "2          13016  41.885919 -87.651133  41.894345 -87.622798        member   \n",
       "3          13134  41.838464 -87.635406  41.881370 -87.674930        member   \n",
       "4          13288  41.895954 -87.667728  41.920082 -87.677855        casual   \n",
       "\n",
       "        ride_time    weekday  \n",
       "0 0 days 00:09:16     Monday  \n",
       "1 0 days 00:26:11     Sunday  \n",
       "2 0 days 00:12:06    Tuesday  \n",
       "3 0 days 00:29:01    Tuesday  \n",
       "4 0 days 00:14:11  Wednesday  "
      ]
     },
     "execution_count": 65,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df1.head()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Limpieza y Transformaación "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Queremos agreagar una columna extra que contenga la duracion de cada viaje. Lo primero es modificar el tipo de datos de object a datetime de las columnas 'started_at' y 'ended_at' "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 181806 entries, 0 to 181805\n",
      "Data columns (total 13 columns):\n",
      " #   Column              Non-Null Count   Dtype         \n",
      "---  ------              --------------   -----         \n",
      " 0   ride_id             181806 non-null  object        \n",
      " 1   rideable_type       181806 non-null  object        \n",
      " 2   started_at          181806 non-null  datetime64[ns]\n",
      " 3   ended_at            181806 non-null  datetime64[ns]\n",
      " 4   start_station_name  152523 non-null  object        \n",
      " 5   start_station_id    152523 non-null  object        \n",
      " 6   end_station_name    150648 non-null  object        \n",
      " 7   end_station_id      150648 non-null  object        \n",
      " 8   start_lat           181806 non-null  float64       \n",
      " 9   start_lng           181806 non-null  float64       \n",
      " 10  end_lat             181678 non-null  float64       \n",
      " 11  end_lng             181678 non-null  float64       \n",
      " 12  member_casual       181806 non-null  object        \n",
      "dtypes: datetime64[ns](2), float64(4), object(7)\n",
      "memory usage: 18.0+ MB\n"
     ]
    }
   ],
   "source": [
    "df1['started_at']= pd.to_datetime(df1['started_at'])\n",
    "df1['ended_at']= pd.to_datetime(df1['ended_at'])\n",
    "df1.info()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Ahora que estan en formato de fecha agregamos otra columa para calcular la duracion de cada viaje. \n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 181806 entries, 0 to 181805\n",
      "Data columns (total 14 columns):\n",
      " #   Column              Non-Null Count   Dtype          \n",
      "---  ------              --------------   -----          \n",
      " 0   ride_id             181806 non-null  object         \n",
      " 1   rideable_type       181806 non-null  object         \n",
      " 2   started_at          181806 non-null  datetime64[ns] \n",
      " 3   ended_at            181806 non-null  datetime64[ns] \n",
      " 4   start_station_name  152523 non-null  object         \n",
      " 5   start_station_id    152523 non-null  object         \n",
      " 6   end_station_name    150648 non-null  object         \n",
      " 7   end_station_id      150648 non-null  object         \n",
      " 8   start_lat           181806 non-null  float64        \n",
      " 9   start_lng           181806 non-null  float64        \n",
      " 10  end_lat             181678 non-null  float64        \n",
      " 11  end_lng             181678 non-null  float64        \n",
      " 12  member_casual       181806 non-null  object         \n",
      " 13  ride_time           181806 non-null  timedelta64[ns]\n",
      "dtypes: datetime64[ns](2), float64(4), object(7), timedelta64[ns](1)\n",
      "memory usage: 19.4+ MB\n"
     ]
    }
   ],
   "source": [
    "df1['ride_time']= df1['ended_at'] - df1['started_at']\n",
    "df1.info()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "ahora añadieremos una columna que nos diga que dia de la semana se efectuo el viaje\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 181806 entries, 0 to 181805\n",
      "Data columns (total 15 columns):\n",
      " #   Column              Non-Null Count   Dtype          \n",
      "---  ------              --------------   -----          \n",
      " 0   ride_id             181806 non-null  object         \n",
      " 1   rideable_type       181806 non-null  object         \n",
      " 2   started_at          181806 non-null  datetime64[ns] \n",
      " 3   ended_at            181806 non-null  datetime64[ns] \n",
      " 4   start_station_name  152523 non-null  object         \n",
      " 5   start_station_id    152523 non-null  object         \n",
      " 6   end_station_name    150648 non-null  object         \n",
      " 7   end_station_id      150648 non-null  object         \n",
      " 8   start_lat           181806 non-null  float64        \n",
      " 9   start_lng           181806 non-null  float64        \n",
      " 10  end_lat             181678 non-null  float64        \n",
      " 11  end_lng             181678 non-null  float64        \n",
      " 12  member_casual       181806 non-null  object         \n",
      " 13  ride_time           181806 non-null  timedelta64[ns]\n",
      " 14  weekday             181806 non-null  object         \n",
      "dtypes: datetime64[ns](2), float64(4), object(8), timedelta64[ns](1)\n",
      "memory usage: 20.8+ MB\n"
     ]
    },
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>ride_id</th>\n",
       "      <th>rideable_type</th>\n",
       "      <th>started_at</th>\n",
       "      <th>ended_at</th>\n",
       "      <th>start_station_name</th>\n",
       "      <th>start_station_id</th>\n",
       "      <th>end_station_name</th>\n",
       "      <th>end_station_id</th>\n",
       "      <th>start_lat</th>\n",
       "      <th>start_lng</th>\n",
       "      <th>end_lat</th>\n",
       "      <th>end_lng</th>\n",
       "      <th>member_casual</th>\n",
       "      <th>ride_time</th>\n",
       "      <th>weekday</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>65DBD2F447EC51C2</td>\n",
       "      <td>electric_bike</td>\n",
       "      <td>2022-12-05 10:47:18</td>\n",
       "      <td>2022-12-05 10:56:34</td>\n",
       "      <td>Clifton Ave &amp; Armitage Ave</td>\n",
       "      <td>TA1307000163</td>\n",
       "      <td>Sedgwick St &amp; Webster Ave</td>\n",
       "      <td>13191</td>\n",
       "      <td>41.918244</td>\n",
       "      <td>-87.657115</td>\n",
       "      <td>41.922167</td>\n",
       "      <td>-87.638888</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:09:16</td>\n",
       "      <td>Monday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>0C201AA7EA0EA1AD</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2022-12-18 06:42:33</td>\n",
       "      <td>2022-12-18 07:08:44</td>\n",
       "      <td>Broadway &amp; Belmont Ave</td>\n",
       "      <td>13277</td>\n",
       "      <td>Sedgwick St &amp; Webster Ave</td>\n",
       "      <td>13191</td>\n",
       "      <td>41.940106</td>\n",
       "      <td>-87.645451</td>\n",
       "      <td>41.922167</td>\n",
       "      <td>-87.638888</td>\n",
       "      <td>casual</td>\n",
       "      <td>0 days 00:26:11</td>\n",
       "      <td>Sunday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>E0B148CCB358A49D</td>\n",
       "      <td>electric_bike</td>\n",
       "      <td>2022-12-13 08:47:45</td>\n",
       "      <td>2022-12-13 08:59:51</td>\n",
       "      <td>Sangamon St &amp; Lake St</td>\n",
       "      <td>TA1306000015</td>\n",
       "      <td>St. Clair St &amp; Erie St</td>\n",
       "      <td>13016</td>\n",
       "      <td>41.885919</td>\n",
       "      <td>-87.651133</td>\n",
       "      <td>41.894345</td>\n",
       "      <td>-87.622798</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:12:06</td>\n",
       "      <td>Tuesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>54C5775D2B7C9188</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2022-12-13 18:50:47</td>\n",
       "      <td>2022-12-13 19:19:48</td>\n",
       "      <td>Shields Ave &amp; 31st St</td>\n",
       "      <td>KA1503000038</td>\n",
       "      <td>Damen Ave &amp; Madison St</td>\n",
       "      <td>13134</td>\n",
       "      <td>41.838464</td>\n",
       "      <td>-87.635406</td>\n",
       "      <td>41.881370</td>\n",
       "      <td>-87.674930</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:29:01</td>\n",
       "      <td>Tuesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>A4891F78776D35DF</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2022-12-14 16:13:39</td>\n",
       "      <td>2022-12-14 16:27:50</td>\n",
       "      <td>Ashland Ave &amp; Chicago Ave</td>\n",
       "      <td>13247</td>\n",
       "      <td>Damen Ave &amp; Charleston St</td>\n",
       "      <td>13288</td>\n",
       "      <td>41.895954</td>\n",
       "      <td>-87.667728</td>\n",
       "      <td>41.920082</td>\n",
       "      <td>-87.677855</td>\n",
       "      <td>casual</td>\n",
       "      <td>0 days 00:14:11</td>\n",
       "      <td>Wednesday</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            ride_id  rideable_type          started_at            ended_at  \\\n",
       "0  65DBD2F447EC51C2  electric_bike 2022-12-05 10:47:18 2022-12-05 10:56:34   \n",
       "1  0C201AA7EA0EA1AD   classic_bike 2022-12-18 06:42:33 2022-12-18 07:08:44   \n",
       "2  E0B148CCB358A49D  electric_bike 2022-12-13 08:47:45 2022-12-13 08:59:51   \n",
       "3  54C5775D2B7C9188   classic_bike 2022-12-13 18:50:47 2022-12-13 19:19:48   \n",
       "4  A4891F78776D35DF   classic_bike 2022-12-14 16:13:39 2022-12-14 16:27:50   \n",
       "\n",
       "           start_station_name start_station_id           end_station_name  \\\n",
       "0  Clifton Ave & Armitage Ave     TA1307000163  Sedgwick St & Webster Ave   \n",
       "1      Broadway & Belmont Ave            13277  Sedgwick St & Webster Ave   \n",
       "2       Sangamon St & Lake St     TA1306000015     St. Clair St & Erie St   \n",
       "3       Shields Ave & 31st St     KA1503000038     Damen Ave & Madison St   \n",
       "4   Ashland Ave & Chicago Ave            13247  Damen Ave & Charleston St   \n",
       "\n",
       "  end_station_id  start_lat  start_lng    end_lat    end_lng member_casual  \\\n",
       "0          13191  41.918244 -87.657115  41.922167 -87.638888        member   \n",
       "1          13191  41.940106 -87.645451  41.922167 -87.638888        casual   \n",
       "2          13016  41.885919 -87.651133  41.894345 -87.622798        member   \n",
       "3          13134  41.838464 -87.635406  41.881370 -87.674930        member   \n",
       "4          13288  41.895954 -87.667728  41.920082 -87.677855        casual   \n",
       "\n",
       "        ride_time    weekday  \n",
       "0 0 days 00:09:16     Monday  \n",
       "1 0 days 00:26:11     Sunday  \n",
       "2 0 days 00:12:06    Tuesday  \n",
       "3 0 days 00:29:01    Tuesday  \n",
       "4 0 days 00:14:11  Wednesday  "
      ]
     },
     "execution_count": 8,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df1['weekday'] = df1['started_at'].dt.day_name()\n",
    "df1.info()\n",
    "df1.head()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Repetimos el proceso para los demas df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [],
   "source": [
    "#Añadimos columna ride_time y weekday a las 12 tablas\n",
    "df2['started_at']= pd.to_datetime(df2['started_at'])\n",
    "df2['ended_at']= pd.to_datetime(df2['ended_at'])\n",
    "df2['ride_time']= df2['ended_at'] - df2['started_at']\n",
    "df2['weekday'] = df2['started_at'].dt.day_name()\n",
    "\n",
    "df3['started_at']= pd.to_datetime(df3['started_at'])\n",
    "df3['ended_at']= pd.to_datetime(df3['ended_at'])\n",
    "df3['ride_time']= df3['ended_at'] - df3['started_at']\n",
    "df3['weekday'] = df3['started_at'].dt.day_name()\n",
    "\n",
    "df4['started_at']= pd.to_datetime(df4['started_at'])\n",
    "df4['ended_at']= pd.to_datetime(df4['ended_at'])\n",
    "df4['ride_time']= df4['ended_at'] - df4['started_at']\n",
    "df4['weekday'] = df4['started_at'].dt.day_name()\n",
    "\n",
    "df5['started_at']= pd.to_datetime(df5['started_at'])\n",
    "df5['ended_at']= pd.to_datetime(df5['ended_at'])\n",
    "df5['ride_time']= df5['ended_at'] - df5['started_at']\n",
    "df5['weekday'] = df5['started_at'].dt.day_name()\n",
    "\n",
    "df6['started_at']= pd.to_datetime(df6['started_at'])\n",
    "df6['ended_at']= pd.to_datetime(df6['ended_at'])\n",
    "df6['ride_time']= df6['ended_at'] - df6['started_at']\n",
    "df6['weekday'] = df6['started_at'].dt.day_name()\n",
    "\n",
    "df7['started_at']= pd.to_datetime(df7['started_at'])\n",
    "df7['ended_at']= pd.to_datetime(df7['ended_at'])\n",
    "df7['ride_time']= df7['ended_at'] - df7['started_at']\n",
    "df7['weekday'] = df7['started_at'].dt.day_name()\n",
    "\n",
    "df8['started_at']= pd.to_datetime(df8['started_at'])\n",
    "df8['ended_at']= pd.to_datetime(df8['ended_at'])\n",
    "df8['ride_time']= df8['ended_at'] - df8['started_at']\n",
    "df8['weekday'] = df8['started_at'].dt.day_name()\n",
    "\n",
    "df9['started_at']= pd.to_datetime(df9['started_at'])\n",
    "df9['ended_at']= pd.to_datetime(df9['ended_at'])\n",
    "df9['ride_time']= df9['ended_at'] - df9['started_at']\n",
    "df9['weekday'] = df9['started_at'].dt.day_name()\n",
    "\n",
    "df10['started_at']= pd.to_datetime(df10['started_at'])\n",
    "df10['ended_at']= pd.to_datetime(df10['ended_at'])\n",
    "df10['ride_time']= df10['ended_at'] - df10['started_at']\n",
    "df10['weekday'] = df10['started_at'].dt.day_name()\n",
    "\n",
    "df11['started_at']= pd.to_datetime(df11['started_at'])\n",
    "df11['ended_at']= pd.to_datetime(df11['ended_at'])\n",
    "df11['ride_time']= df11['ended_at'] - df11['started_at']\n",
    "df11['weekday'] = df11['started_at'].dt.day_name()\n",
    "\n",
    "df12['started_at']= pd.to_datetime(df12['started_at'])\n",
    "df12['ended_at']= pd.to_datetime(df12['ended_at'])\n",
    "df12['ride_time']= df12['ended_at'] - df12['started_at']\n",
    "df12['weekday'] = df12['started_at'].dt.day_name()\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>ride_id</th>\n",
       "      <th>rideable_type</th>\n",
       "      <th>started_at</th>\n",
       "      <th>ended_at</th>\n",
       "      <th>start_station_name</th>\n",
       "      <th>start_station_id</th>\n",
       "      <th>end_station_name</th>\n",
       "      <th>end_station_id</th>\n",
       "      <th>start_lat</th>\n",
       "      <th>start_lng</th>\n",
       "      <th>end_lat</th>\n",
       "      <th>end_lng</th>\n",
       "      <th>member_casual</th>\n",
       "      <th>ride_time</th>\n",
       "      <th>weekday</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>CBCD0D7777F0E45F</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2023-02-14 11:59:42</td>\n",
       "      <td>2023-02-14 12:13:38</td>\n",
       "      <td>Southport Ave &amp; Clybourn Ave</td>\n",
       "      <td>TA1309000030</td>\n",
       "      <td>Clark St &amp; Schiller St</td>\n",
       "      <td>TA1309000024</td>\n",
       "      <td>41.920771</td>\n",
       "      <td>-87.663712</td>\n",
       "      <td>41.907993</td>\n",
       "      <td>-87.631501</td>\n",
       "      <td>casual</td>\n",
       "      <td>0 days 00:13:56</td>\n",
       "      <td>Tuesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>F3EC5FCE5FF39DE9</td>\n",
       "      <td>electric_bike</td>\n",
       "      <td>2023-02-15 13:53:48</td>\n",
       "      <td>2023-02-15 13:59:08</td>\n",
       "      <td>Clarendon Ave &amp; Gordon Ter</td>\n",
       "      <td>13379</td>\n",
       "      <td>Sheridan Rd &amp; Lawrence Ave</td>\n",
       "      <td>TA1309000041</td>\n",
       "      <td>41.957879</td>\n",
       "      <td>-87.649584</td>\n",
       "      <td>41.969517</td>\n",
       "      <td>-87.654691</td>\n",
       "      <td>casual</td>\n",
       "      <td>0 days 00:05:20</td>\n",
       "      <td>Wednesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>E54C1F27FA9354FF</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2023-02-19 11:10:57</td>\n",
       "      <td>2023-02-19 11:35:01</td>\n",
       "      <td>Southport Ave &amp; Clybourn Ave</td>\n",
       "      <td>TA1309000030</td>\n",
       "      <td>Aberdeen St &amp; Monroe St</td>\n",
       "      <td>13156</td>\n",
       "      <td>41.920771</td>\n",
       "      <td>-87.663712</td>\n",
       "      <td>41.880419</td>\n",
       "      <td>-87.655519</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:24:04</td>\n",
       "      <td>Sunday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>3D561E04F739CC45</td>\n",
       "      <td>electric_bike</td>\n",
       "      <td>2023-02-26 16:12:05</td>\n",
       "      <td>2023-02-26 16:39:55</td>\n",
       "      <td>Southport Ave &amp; Clybourn Ave</td>\n",
       "      <td>TA1309000030</td>\n",
       "      <td>Franklin St &amp; Adams St (Temp)</td>\n",
       "      <td>TA1309000008</td>\n",
       "      <td>41.920873</td>\n",
       "      <td>-87.663733</td>\n",
       "      <td>41.879434</td>\n",
       "      <td>-87.635504</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:27:50</td>\n",
       "      <td>Sunday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>0CB4B4D53B2DBE05</td>\n",
       "      <td>electric_bike</td>\n",
       "      <td>2023-02-20 11:55:23</td>\n",
       "      <td>2023-02-20 12:05:48</td>\n",
       "      <td>Prairie Ave &amp; Garfield Blvd</td>\n",
       "      <td>TA1307000160</td>\n",
       "      <td>Cottage Grove Ave &amp; 63rd St</td>\n",
       "      <td>KA1503000054</td>\n",
       "      <td>41.794827</td>\n",
       "      <td>-87.618795</td>\n",
       "      <td>41.780531</td>\n",
       "      <td>-87.605970</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:10:25</td>\n",
       "      <td>Monday</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            ride_id  rideable_type          started_at            ended_at  \\\n",
       "0  CBCD0D7777F0E45F   classic_bike 2023-02-14 11:59:42 2023-02-14 12:13:38   \n",
       "1  F3EC5FCE5FF39DE9  electric_bike 2023-02-15 13:53:48 2023-02-15 13:59:08   \n",
       "2  E54C1F27FA9354FF   classic_bike 2023-02-19 11:10:57 2023-02-19 11:35:01   \n",
       "3  3D561E04F739CC45  electric_bike 2023-02-26 16:12:05 2023-02-26 16:39:55   \n",
       "4  0CB4B4D53B2DBE05  electric_bike 2023-02-20 11:55:23 2023-02-20 12:05:48   \n",
       "\n",
       "             start_station_name start_station_id  \\\n",
       "0  Southport Ave & Clybourn Ave     TA1309000030   \n",
       "1    Clarendon Ave & Gordon Ter            13379   \n",
       "2  Southport Ave & Clybourn Ave     TA1309000030   \n",
       "3  Southport Ave & Clybourn Ave     TA1309000030   \n",
       "4   Prairie Ave & Garfield Blvd     TA1307000160   \n",
       "\n",
       "                end_station_name end_station_id  start_lat  start_lng  \\\n",
       "0         Clark St & Schiller St   TA1309000024  41.920771 -87.663712   \n",
       "1     Sheridan Rd & Lawrence Ave   TA1309000041  41.957879 -87.649584   \n",
       "2        Aberdeen St & Monroe St          13156  41.920771 -87.663712   \n",
       "3  Franklin St & Adams St (Temp)   TA1309000008  41.920873 -87.663733   \n",
       "4    Cottage Grove Ave & 63rd St   KA1503000054  41.794827 -87.618795   \n",
       "\n",
       "     end_lat    end_lng member_casual       ride_time    weekday  \n",
       "0  41.907993 -87.631501        casual 0 days 00:13:56    Tuesday  \n",
       "1  41.969517 -87.654691        casual 0 days 00:05:20  Wednesday  \n",
       "2  41.880419 -87.655519        member 0 days 00:24:04     Sunday  \n",
       "3  41.879434 -87.635504        member 0 days 00:27:50     Sunday  \n",
       "4  41.780531 -87.605970        member 0 days 00:10:25     Monday  "
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df3.head()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Ahora uniremos los df en un solo df llamado All_Trips, que contenga los viajes realizados en 12 meses del año 2023. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>ride_id</th>\n",
       "      <th>rideable_type</th>\n",
       "      <th>started_at</th>\n",
       "      <th>ended_at</th>\n",
       "      <th>start_station_name</th>\n",
       "      <th>start_station_id</th>\n",
       "      <th>end_station_name</th>\n",
       "      <th>end_station_id</th>\n",
       "      <th>start_lat</th>\n",
       "      <th>start_lng</th>\n",
       "      <th>end_lat</th>\n",
       "      <th>end_lng</th>\n",
       "      <th>member_casual</th>\n",
       "      <th>ride_time</th>\n",
       "      <th>weekday</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>65DBD2F447EC51C2</td>\n",
       "      <td>electric_bike</td>\n",
       "      <td>2022-12-05 10:47:18</td>\n",
       "      <td>2022-12-05 10:56:34</td>\n",
       "      <td>Clifton Ave &amp; Armitage Ave</td>\n",
       "      <td>TA1307000163</td>\n",
       "      <td>Sedgwick St &amp; Webster Ave</td>\n",
       "      <td>13191</td>\n",
       "      <td>41.918244</td>\n",
       "      <td>-87.657115</td>\n",
       "      <td>41.922167</td>\n",
       "      <td>-87.638888</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:09:16</td>\n",
       "      <td>Monday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>0C201AA7EA0EA1AD</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2022-12-18 06:42:33</td>\n",
       "      <td>2022-12-18 07:08:44</td>\n",
       "      <td>Broadway &amp; Belmont Ave</td>\n",
       "      <td>13277</td>\n",
       "      <td>Sedgwick St &amp; Webster Ave</td>\n",
       "      <td>13191</td>\n",
       "      <td>41.940106</td>\n",
       "      <td>-87.645451</td>\n",
       "      <td>41.922167</td>\n",
       "      <td>-87.638888</td>\n",
       "      <td>casual</td>\n",
       "      <td>0 days 00:26:11</td>\n",
       "      <td>Sunday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>E0B148CCB358A49D</td>\n",
       "      <td>electric_bike</td>\n",
       "      <td>2022-12-13 08:47:45</td>\n",
       "      <td>2022-12-13 08:59:51</td>\n",
       "      <td>Sangamon St &amp; Lake St</td>\n",
       "      <td>TA1306000015</td>\n",
       "      <td>St. Clair St &amp; Erie St</td>\n",
       "      <td>13016</td>\n",
       "      <td>41.885919</td>\n",
       "      <td>-87.651133</td>\n",
       "      <td>41.894345</td>\n",
       "      <td>-87.622798</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:12:06</td>\n",
       "      <td>Tuesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>54C5775D2B7C9188</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2022-12-13 18:50:47</td>\n",
       "      <td>2022-12-13 19:19:48</td>\n",
       "      <td>Shields Ave &amp; 31st St</td>\n",
       "      <td>KA1503000038</td>\n",
       "      <td>Damen Ave &amp; Madison St</td>\n",
       "      <td>13134</td>\n",
       "      <td>41.838464</td>\n",
       "      <td>-87.635406</td>\n",
       "      <td>41.881370</td>\n",
       "      <td>-87.674930</td>\n",
       "      <td>member</td>\n",
       "      <td>0 days 00:29:01</td>\n",
       "      <td>Tuesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>A4891F78776D35DF</td>\n",
       "      <td>classic_bike</td>\n",
       "      <td>2022-12-14 16:13:39</td>\n",
       "      <td>2022-12-14 16:27:50</td>\n",
       "      <td>Ashland Ave &amp; Chicago Ave</td>\n",
       "      <td>13247</td>\n",
       "      <td>Damen Ave &amp; Charleston St</td>\n",
       "      <td>13288</td>\n",
       "      <td>41.895954</td>\n",
       "      <td>-87.667728</td>\n",
       "      <td>41.920082</td>\n",
       "      <td>-87.677855</td>\n",
       "      <td>casual</td>\n",
       "      <td>0 days 00:14:11</td>\n",
       "      <td>Wednesday</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            ride_id  rideable_type          started_at            ended_at  \\\n",
       "0  65DBD2F447EC51C2  electric_bike 2022-12-05 10:47:18 2022-12-05 10:56:34   \n",
       "1  0C201AA7EA0EA1AD   classic_bike 2022-12-18 06:42:33 2022-12-18 07:08:44   \n",
       "2  E0B148CCB358A49D  electric_bike 2022-12-13 08:47:45 2022-12-13 08:59:51   \n",
       "3  54C5775D2B7C9188   classic_bike 2022-12-13 18:50:47 2022-12-13 19:19:48   \n",
       "4  A4891F78776D35DF   classic_bike 2022-12-14 16:13:39 2022-12-14 16:27:50   \n",
       "\n",
       "           start_station_name start_station_id           end_station_name  \\\n",
       "0  Clifton Ave & Armitage Ave     TA1307000163  Sedgwick St & Webster Ave   \n",
       "1      Broadway & Belmont Ave            13277  Sedgwick St & Webster Ave   \n",
       "2       Sangamon St & Lake St     TA1306000015     St. Clair St & Erie St   \n",
       "3       Shields Ave & 31st St     KA1503000038     Damen Ave & Madison St   \n",
       "4   Ashland Ave & Chicago Ave            13247  Damen Ave & Charleston St   \n",
       "\n",
       "  end_station_id  start_lat  start_lng    end_lat    end_lng member_casual  \\\n",
       "0          13191  41.918244 -87.657115  41.922167 -87.638888        member   \n",
       "1          13191  41.940106 -87.645451  41.922167 -87.638888        casual   \n",
       "2          13016  41.885919 -87.651133  41.894345 -87.622798        member   \n",
       "3          13134  41.838464 -87.635406  41.881370 -87.674930        member   \n",
       "4          13288  41.895954 -87.667728  41.920082 -87.677855        casual   \n",
       "\n",
       "        ride_time    weekday  \n",
       "0 0 days 00:09:16     Monday  \n",
       "1 0 days 00:26:11     Sunday  \n",
       "2 0 days 00:12:06    Tuesday  \n",
       "3 0 days 00:29:01    Tuesday  \n",
       "4 0 days 00:14:11  Wednesday  "
      ]
     },
     "execution_count": 11,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "all_trips = pd.concat([df1, df2,df3, df4, df5, df6, df7, df8, df9, df10, df11, df12])\n",
    "all_trips.head()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Eliminaremos valores nulos y valores duplicados"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "valores duplicados: 0\n"
     ]
    },
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>ride_id</th>\n",
       "      <th>rideable_type</th>\n",
       "      <th>started_at</th>\n",
       "      <th>ended_at</th>\n",
       "      <th>start_station_name</th>\n",
       "      <th>start_station_id</th>\n",
       "      <th>end_station_name</th>\n",
       "      <th>end_station_id</th>\n",
       "      <th>start_lat</th>\n",
       "      <th>start_lng</th>\n",
       "      <th>end_lat</th>\n",
       "      <th>end_lng</th>\n",
       "      <th>member_casual</th>\n",
       "      <th>ride_time</th>\n",
       "      <th>weekday</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "Empty DataFrame\n",
       "Columns: [ride_id, rideable_type, started_at, ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, ride_time, weekday]\n",
       "Index: []"
      ]
     },
     "execution_count": 12,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#valores duplicados\n",
    "n_duplicated = all_trips.duplicated().sum()\n",
    "print(f\"valores duplicados: {n_duplicated}\")\n",
    "\n",
    "all_trips[all_trips.duplicated]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "ride_id                    0\n",
       "rideable_type              0\n",
       "started_at                 0\n",
       "ended_at                   0\n",
       "start_station_name    869289\n",
       "start_station_id      869421\n",
       "end_station_name      922436\n",
       "end_station_id        922577\n",
       "start_lat                  0\n",
       "start_lng                  0\n",
       "end_lat                 6879\n",
       "end_lng                 6879\n",
       "member_casual              0\n",
       "ride_time                  0\n",
       "weekday                    0\n",
       "dtype: int64"
      ]
     },
     "execution_count": 13,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#valores faltantes\n",
    "all_trips.isna().sum()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Tenemos valores nulos en las columnas start_station_name, start_station_id, end_station_name, end_station_id, end_lat, end_lng. Vamos a crear otro df que remueva esos valores nulos. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "ride_id               0\n",
       "rideable_type         0\n",
       "started_at            0\n",
       "ended_at              0\n",
       "start_station_name    0\n",
       "start_station_id      0\n",
       "end_station_name      0\n",
       "end_station_id        0\n",
       "start_lat             0\n",
       "start_lng             0\n",
       "end_lat               0\n",
       "end_lng               0\n",
       "member_casual         0\n",
       "ride_time             0\n",
       "weekday               0\n",
       "dtype: int64"
      ]
     },
     "execution_count": 14,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "c_all_trips = all_trips.dropna()\n",
    "c_all_trips.isna().sum()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Analisis de Datos "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Ahora tenemos todos los datos reuinidos y propiamente limpios y validados podemos comenzar el analisis. Se dividira en 5 consultas. Calcularemos:\n",
    "1. Promedio de duracion de viajes de la variable ride_time, \n",
    "2. Moda de la variable weekday, \n",
    "3. Porcentaje de usuarios habituales. \n",
    "4. Promedio de la duracion de viajes para usuarios casuales y habituales. \n",
    "5. Cantidad de viajes por dia de la semana realizadas por usuarios casuales y habituales. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 1. Promedio de la duración de viajes\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>started_at</th>\n",
       "      <th>ended_at</th>\n",
       "      <th>start_lat</th>\n",
       "      <th>start_lng</th>\n",
       "      <th>end_lat</th>\n",
       "      <th>end_lng</th>\n",
       "      <th>ride_time</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>4299967</td>\n",
       "      <td>4299967</td>\n",
       "      <td>4.299967e+06</td>\n",
       "      <td>4.299967e+06</td>\n",
       "      <td>4.299967e+06</td>\n",
       "      <td>4.299967e+06</td>\n",
       "      <td>4299967</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>2023-07-03 03:47:14.904931072</td>\n",
       "      <td>2023-07-03 04:03:12.263578880</td>\n",
       "      <td>4.190095e+01</td>\n",
       "      <td>-8.764464e+01</td>\n",
       "      <td>4.190137e+01</td>\n",
       "      <td>-8.764486e+01</td>\n",
       "      <td>0 days 00:15:57.358648101</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>2022-12-01 00:01:22</td>\n",
       "      <td>2022-12-01 00:03:41</td>\n",
       "      <td>4.164850e+01</td>\n",
       "      <td>-8.784409e+01</td>\n",
       "      <td>0.000000e+00</td>\n",
       "      <td>-8.784406e+01</td>\n",
       "      <td>-1 days +23:05:26</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>2023-05-10 07:21:06.500000</td>\n",
       "      <td>2023-05-10 07:31:49</td>\n",
       "      <td>4.188084e+01</td>\n",
       "      <td>-8.765762e+01</td>\n",
       "      <td>4.188096e+01</td>\n",
       "      <td>-8.765842e+01</td>\n",
       "      <td>0 days 00:05:37</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>2023-07-12 16:52:18</td>\n",
       "      <td>2023-07-12 17:04:54</td>\n",
       "      <td>4.189636e+01</td>\n",
       "      <td>-8.764170e+01</td>\n",
       "      <td>4.189662e+01</td>\n",
       "      <td>-8.764182e+01</td>\n",
       "      <td>0 days 00:09:48</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>2023-09-07 07:39:31.500000</td>\n",
       "      <td>2023-09-07 07:51:02.500000</td>\n",
       "      <td>4.192731e+01</td>\n",
       "      <td>-8.762858e+01</td>\n",
       "      <td>4.192877e+01</td>\n",
       "      <td>-8.762858e+01</td>\n",
       "      <td>0 days 00:17:29</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>2023-11-30 23:58:38</td>\n",
       "      <td>2023-12-01 09:47:35</td>\n",
       "      <td>4.206485e+01</td>\n",
       "      <td>-8.752823e+01</td>\n",
       "      <td>4.206485e+01</td>\n",
       "      <td>0.000000e+00</td>\n",
       "      <td>8 days 10:16:18</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>4.303152e-02</td>\n",
       "      <td>2.489457e-02</td>\n",
       "      <td>5.559158e-02</td>\n",
       "      <td>7.737307e-02</td>\n",
       "      <td>0 days 00:35:58.577397501</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                          started_at                       ended_at  \\\n",
       "count                        4299967                        4299967   \n",
       "mean   2023-07-03 03:47:14.904931072  2023-07-03 04:03:12.263578880   \n",
       "min              2022-12-01 00:01:22            2022-12-01 00:03:41   \n",
       "25%       2023-05-10 07:21:06.500000            2023-05-10 07:31:49   \n",
       "50%              2023-07-12 16:52:18            2023-07-12 17:04:54   \n",
       "75%       2023-09-07 07:39:31.500000     2023-09-07 07:51:02.500000   \n",
       "max              2023-11-30 23:58:38            2023-12-01 09:47:35   \n",
       "std                              NaN                            NaN   \n",
       "\n",
       "          start_lat     start_lng       end_lat       end_lng  \\\n",
       "count  4.299967e+06  4.299967e+06  4.299967e+06  4.299967e+06   \n",
       "mean   4.190095e+01 -8.764464e+01  4.190137e+01 -8.764486e+01   \n",
       "min    4.164850e+01 -8.784409e+01  0.000000e+00 -8.784406e+01   \n",
       "25%    4.188084e+01 -8.765762e+01  4.188096e+01 -8.765842e+01   \n",
       "50%    4.189636e+01 -8.764170e+01  4.189662e+01 -8.764182e+01   \n",
       "75%    4.192731e+01 -8.762858e+01  4.192877e+01 -8.762858e+01   \n",
       "max    4.206485e+01 -8.752823e+01  4.206485e+01  0.000000e+00   \n",
       "std    4.303152e-02  2.489457e-02  5.559158e-02  7.737307e-02   \n",
       "\n",
       "                       ride_time  \n",
       "count                    4299967  \n",
       "mean   0 days 00:15:57.358648101  \n",
       "min            -1 days +23:05:26  \n",
       "25%              0 days 00:05:37  \n",
       "50%              0 days 00:09:48  \n",
       "75%              0 days 00:17:29  \n",
       "max              8 days 10:16:18  \n",
       "std    0 days 00:35:58.577397501  "
      ]
     },
     "execution_count": 22,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "c_all_trips.describe()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Podemos ver que el total de viajes en el año es: 4,299,967 \n",
    "el promedio de duracion es: 16 min\n",
    "el 25% de los viajes se encuentra en el rango de 0 a 6 minutos \n",
    "el 50% de los viajes se encuentra en el rango de 0 a 10 minutos \n",
    "el 75% de los viajes se encuentra en el rango de 0 a 18 minutos "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Agrupamamos en una tabla para la parte de visualizacion"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Graficamos "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 86,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "\n",
    "\n",
    "# Suponiendo que ride_times contiene la duración de los viajes (tipo timedelta)\n",
    "# Convertir la duración de los viajes a minutos\n",
    "ride_times_minutes = c_all_trips['ride_time'] / pd.Timedelta(minutes=1)\n",
    "\n",
    "# Definir los intervalos hasta 18 minutos\n",
    "intervalos = [0, 6, 10, 18]\n",
    "\n",
    "# Contar la cantidad de viajes en cada intervalo\n",
    "frecuencias, bordes = np.histogram(ride_times_minutes, bins=intervalos)\n",
    "\n",
    "# Crear el gráfico de barras\n",
    "plt.bar(range(len(intervalos) - 1), frecuencias, align='center', color='skyblue', edgecolor='black')\n",
    "\n",
    "# Etiquetas y título\n",
    "plt.xlabel('Intervalos de Duración de los Viajes (minutos)')\n",
    "plt.ylabel('Cantidad de Viajes(Millones)')\n",
    "plt.title('Distribución de Duración de los Viajes')\n",
    "\n",
    "# Añadir etiquetas de los intervalos\n",
    "plt.xticks(range(len(intervalos) - 1), ['0-6 min', '6-10 min', '10-18 min'])\n",
    "\n",
    "# Ajustar el rango del eje Y para incluir la cantidad total de viajes\n",
    "plt.ylim(0, c_all_trips.shape[0])\n",
    "\n",
    "# Mostrar el gráfico\n",
    "plt.show()\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 2. Moda de la variable weekday"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 47,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "La moda es: Saturday\n"
     ]
    }
   ],
   "source": [
    "\n",
    "weekday_mode = c_all_trips['weekday'].mode()[0]\n",
    "\n",
    "print(\"La moda es:\", weekday_mode)\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Queremos saber cantidad de viajes por día"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 46,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Cantidad de viajes por día de la semana:\n",
      "weekday\n",
      "Saturday     654440\n",
      "Thursday     651076\n",
      "Tuesday      629964\n",
      "Wednesday    628730\n",
      "Friday       619561\n",
      "Monday       559734\n",
      "Sunday       556462\n",
      "Name: count, dtype: int64\n"
     ]
    }
   ],
   "source": [
    "#\n",
    "day_trips = c_all_trips['weekday'].value_counts()\n",
    "\n",
    "print(\"Cantidad de viajes por día de la semana:\")\n",
    "print(day_trips)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Validamos el total de vaiejes "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 50,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "4299967"
      ]
     },
     "execution_count": 50,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "day_trips.sum()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Graficamos "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 45,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "import matplotlib.pyplot as plt\n",
    "\n",
    "# Suponiendo que 'weekday' es el nombre de la columna que contiene el día de la semana\n",
    "day_trips = c_all_trips['weekday'].value_counts()\n",
    "\n",
    "# Crear el gráfico de barras\n",
    "plt.bar(day_trips.index, day_trips.values, color='skyblue', edgecolor='black')\n",
    "\n",
    "# Etiquetas y título\n",
    "plt.xlabel('Día de la semana')\n",
    "plt.ylabel('Cantidad de viajes')\n",
    "plt.title('Cantidad de viajes por día de la semana')\n",
    "\n",
    "# Mostrar el gráfico\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 3. Porcentaje de viajes realizados por miembros y por usuarios casuales. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Contamos valores "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 71,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Total de viajes</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>member_casual</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>member</th>\n",
       "      <td>2773391</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>casual</th>\n",
       "      <td>1526576</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "               Total de viajes\n",
       "member_casual                 \n",
       "member                 2773391\n",
       "casual                 1526576"
      ]
     },
     "execution_count": 71,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "members = c_all_trips['member_casual'].value_counts()\n",
    "\n",
    "# Convertir la Serie a un DataFrame\n",
    "members_df = pd.DataFrame(members)\n",
    "\n",
    "members_df = members_df.rename(columns={'member_casual': 'Tipo de miembro', 'count': 'Total de viajes'})\n",
    "\n",
    "# Imprimir el DataFrame con los nuevos nombres de columnas\n",
    "members_df"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Validamos con el total de viajes "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 72,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "4299967"
      ]
     },
     "execution_count": 72,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "total_trips = members.sum()\n",
    "total_trips \n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Calculamos el porcentaje de miembros casuales y habituales con respecto al total de viajes "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 74,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "64.49796010062403\n",
      "35.50203989937597\n"
     ]
    }
   ],
   "source": [
    "member_percent = members['member'] / total_trips *100\n",
    "casual_percent = members['casual'] / total_trips *100\n",
    "\n",
    "print(member_percent)\n",
    "print(casual_percent)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Graficamos "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 49,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "labels = ['Miembros', 'Clientes Casuales']\n",
    "sizes = [member_percent, casual_percent]\n",
    "colors = ['lightblue', 'lightcoral']\n",
    "explode = (0.1, 0)  # Explotar la primera porción (miembros)\n",
    "\n",
    "# Crear el gráfico circular\n",
    "plt.pie(sizes, explode=explode, labels=labels, colors=colors, autopct='%1.1f%%', startangle=140)\n",
    "\n",
    "# Añadir un título\n",
    "plt.title('Porcentaje de Viajes por Tipo de Usuario')\n",
    "\n",
    "# Mostrar el gráfico\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 4.Promedio de la duracion de viajes para usuarios casuales y habituales. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 52,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Promedio de duración de viajes para miembros: 0 days 00:12:07.265058551\n",
      "Promedio de duración de viajes para ciclistas ocasionales: 0 days 00:22:55.378773149\n"
     ]
    }
   ],
   "source": [
    "\n",
    "\n",
    "# Calcular el promedio de la duración de los viajes para miembros\n",
    "avg_members = c_all_trips[c_all_trips['member_casual'] == 'member']['ride_time'].mean()\n",
    "\n",
    "# Calcular el promedio de la duración de los viajes para ciclistas ocasionales\n",
    "avg_casual = c_all_trips[c_all_trips['member_casual'] == 'casual']['ride_time'].mean()\n",
    "\n",
    "print(\"Promedio de duración de viajes para miembros:\", avg_members)\n",
    "print(\"Promedio de duración de viajes para ciclistas ocasionales:\", avg_casual)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 5. Cantidad de viajes por dia de la semana realizadas por usuarios casuales y habituales. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Agrupar los datos por día de la semana y calcular el promedio de ride_time para cada grupo"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 54,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Promedio de ride_time por día de la semana:\n",
      "weekday\n",
      "Friday      0 days 00:15:48.417335823\n",
      "Monday      0 days 00:14:57.789296344\n",
      "Saturday    0 days 00:19:24.464902817\n",
      "Sunday      0 days 00:19:30.229595192\n",
      "Thursday    0 days 00:14:08.265698628\n",
      "Tuesday     0 days 00:14:11.144616200\n",
      "Wednesday   0 days 00:13:54.616433127\n",
      "Name: ride_time, dtype: timedelta64[ns]\n"
     ]
    }
   ],
   "source": [
    "avg_ride_time_day = c_all_trips.groupby('weekday')['ride_time'].mean()\n",
    "\n",
    "print(\"Promedio de ride_time por día de la semana:\")\n",
    "print(avg_ride_time_day)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Agrupar los datos por día de la semana y calcular el recuento de trip_id para cada grupo"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 78,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Número de viajes por día de la semana:\n",
      "weekday\n",
      "Friday       619561\n",
      "Monday       559734\n",
      "Saturday     654440\n",
      "Sunday       556462\n",
      "Thursday     651076\n",
      "Tuesday      629964\n",
      "Wednesday    628730\n",
      "Name: ride_id, dtype: int64\n"
     ]
    }
   ],
   "source": [
    "viajes_por_dia = c_all_trips.groupby('weekday')['ride_id'].count()\n",
    "\n",
    "print(\"Número de viajes por día de la semana:\")\n",
    "print(viajes_por_dia)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Filtrar los datos para usuarios ocasionales ('casual')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 82,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Número de viajes por día de la semana para usuarios ocasionales agrupados por ride_id:\n",
      "weekday    member_casual\n",
      "Friday     casual           226195\n",
      "Monday     casual           175301\n",
      "Saturday   casual           308670\n",
      "Sunday     casual           253201\n",
      "Thursday   casual           199333\n",
      "Tuesday    casual           181877\n",
      "Wednesday  casual           181999\n",
      "Name: ride_id, dtype: int64\n"
     ]
    }
   ],
   "source": [
    "# Filtrar los datos para usuarios ocasionales ('casual')\n",
    "viajes_ocasionales = c_all_trips[c_all_trips['member_casual'] == 'casual']\n",
    "\n",
    "# Agrupar por día de la semana y contar los ride_id únicos para cada grupo\n",
    "viajes_por_dia_ocasionales = viajes_ocasionales.groupby(['weekday', 'member_casual'])['ride_id'].count()\n",
    "\n",
    "print(\"Número de viajes por día de la semana para usuarios ocasionales agrupados por ride_id:\")\n",
    "print(viajes_por_dia_ocasionales)\n",
    "\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Podemos observar que la mayor cantidad de viajes por miembros casuales se realiza Sabado y domingo "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Ahora filtramos los datos para miembros habituales ('member')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 84,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Número de viajes por día de la semana para usuarios habituales\n",
      "weekday    member_casual\n",
      "Friday     member           393366\n",
      "Monday     member           384433\n",
      "Saturday   member           345770\n",
      "Sunday     member           303261\n",
      "Thursday   member           451743\n",
      "Tuesday    member           448087\n",
      "Wednesday  member           446731\n",
      "Name: ride_id, dtype: int64\n"
     ]
    }
   ],
   "source": [
    "\n",
    "viajes_miembros  = c_all_trips[c_all_trips['member_casual'] == 'member']\n",
    "\n",
    "# Agrupar por día de la semana y contar los ride_id únicos para cada grupo\n",
    "viajes_por_dia_miembros = viajes_miembros.groupby(['weekday', 'member_casual'])['ride_id'].count()\n",
    "\n",
    "print(\"Número de viajes por día de la semana para usuarios habituales\")\n",
    "print(viajes_por_dia_miembros)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Podemos observar que la mayor cantidad de viajes por miembros se realiza los dias martes, miercoles y jueves. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Conclusiones"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "1. Total viajes 2023 = 4,299,967\n",
    "2. Promedio duracion de viaje 2023 = 16 minutos\n",
    "3. Dia con mayor cantidad de viajes sabado con 654,440\n",
    "4. Dia con menor cantida de viajes domingo con 556,462\n",
    "5. 64.5% de los viajes realizados por Miembros \n",
    "6. 35.5% de los viajes relizados por Casuales \n",
    "7. Promedio de duración de viajes para miembros: 12 minutos\n",
    "8. Promedio de duración de viajes para Casuales 23 minutos \n",
    "9. Dia de a semana con mas viajes por Casuales Sabado con 308,670 y  domingo con 253,201\n",
    "10. Dia de la semana con mas viajes por Miembros Jueves con 451,743 Martes con 448,087  y Miercoles con  446,731\n",
    "\n",
    "\n",
    "Sugerencias de acciones basadas en datos. \n",
    "\n",
    "1. Los datos muestran que los usuarios Casuales utilizan los servicios de bicicleta el sabdo y domingo, pero no entre semana, mientras que los Miembros utilizan mitad de semana. Lo que puede indicar que los casuales lo utilizan en dias de descanso y los miembros en días laborales. Lo que puede indicar que los miembros utilizan los servicios de bicicleta para trasladarse a su trabajo o a la escuela, habrá que realziar encuestas para indicar con que grado de probailidad se cumple. De ser así, una estrategiad de marketing para aumentar los miembros es incentivar a los casuales a utilizar la bicicleta entre semana para trasladarse en bicicleta al trabajo o escuela. \n",
    "\n",
    "2. Incentivar el uso de la bicileta entre semana tambien añadiendo descuentos para usuarios ocacionales entre semana.\n",
    "\n",
    "\n"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.6"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
ipynb…]()
