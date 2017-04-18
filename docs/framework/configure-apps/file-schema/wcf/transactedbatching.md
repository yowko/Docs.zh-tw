---
title: "&lt;transactedBatching&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;transactedBatching&gt;
指定是否支援接收作業的交易批次處理。  
  
## 語法  
  
```  
  
<transactedBatching maxBatchSize="Integer" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`maxBatchSize`|整數，指定可在一個交易中批次處理的接收作業數目上限。  預設值為 0。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## 備註  
 以交易批次設定的傳輸，會嘗試將數個接收作業批次到一個交易中。  如此一來，即可避免在每個接收作業中建立並認可交易時的相對高成本。  
  
## 範例  
 下列範例會示範如何在組態檔中將交易的批次處理行為加入至服務。  
  
```  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <host>  
        <baseAddresses>  
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
        </baseAddresses>  
      </host>  
  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />  
  
      <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="endpointBehavior">  
        <transactedBatching maxBatchSize="10" />  
      </behavior>  
    </endpointBehaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>   
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>