---
title: 在組態檔中設定探索
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ba224bbf27e5a61168040c944bb940c3e6b0d8c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-discovery-in-a-configuration-file"></a>在組態檔中設定探索
探索中使用四個主要的組態設定群組。 本主題將簡要說明各群組，並且顯示如何設定這些群組的範例。 各節後面會有一個連結，可提供與各領域更為深入的文件。  
  
## <a name="behavior-configuration"></a>行為組態  
 探索會使用服務行為和端點行為。 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 行為會啟用服務所有端點的探索，並且讓您指定公告端點。  下列範例示範如何加入 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 並指定公告端點。  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
```  
  
 指定此行為之後，請從 <`service`> 項目參考該行為，如下列範例所示。  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
         <!-- Application Endpoint -->  
         <endpoint address="endpoint0"  
                   binding="basicHttpBinding"  
                   contract="IHelloWorldService" />  
         <!-- Discovery Endpoints -->  
         <endpoint kind="udpDiscoveryEndpoint" />  
        </service>  
    </service>  
```  
  
 為了讓服務能夠探索，您還必須加入探索端點，上述範例即加入了 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 標準端點。  
  
 當您加入公告端點時，也必須將公告接聽程式服務加入至 <`services`> 項目，如下列範例所示。  
  
```xml  
<services>  
   <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
      <!-- Application Endpoint -->  
      <endpoint address="endpoint0"  
                binding="basicHttpBinding"  
                contract="IHelloWorldService" />  
      <!-- Discovery Endpoints -->  
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <!-- Announcement Listener Configuration -->  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
```  
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 行為可用來啟用或停用特定端點的探索。  下列範例設定服務的兩個應用程式端點，其中一個會啟用探索，另一個則停用探索。 請為各端點加入 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 行為。  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService"  
               behaviorConfiguration="helloWorldServiceBehavior">  
  
        <!-- Application Endpoints -->  
        <endpoint address="endpoint0"  
                 binding="basicHttpBinding"  
                 contract="IHelloWorldService"   
                 behaviorConfiguration="ep0Behavior" />  
  
        <endpoint address="endpoint1"  
                  binding="basicHttpBinding"  
                  contract="IHelloWorldService"  
                  behaviorConfiguration="ep1Behavior" />  
  
        <!-- Discovery Endpoints -->  
        <endpoint kind="udpDiscoveryEndpoint" />  
      </service>  
   </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery />  
        </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="ep0Behavior">  
          <endpointDiscovery enabled="true"/>  
        </behavior>  
        <behavior name="ep1Behavior">  
          <endpointDiscovery enabled="false"/>  
        </behavior>  
     </endpointBehaviors>  
   </behaviors>  
```  
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 行為也可以用來將自訂中繼資料加入至服務傳回的端點中繼資料。 下列範例顯示如何執行這項工作。  
  
```xml  
<behavior name="ep4Behavior">  
   <endpointDiscovery enabled="true">  
      <extensions>  
         <CustomMetadata>This is custom metadata.</CustomMetadata>  
         <d:Types xmlns:d="http://schemas.xmlsoap.org/ws/2005/04/discovery" xmlns:i="http://printer.example.org/2003/imaging">i:PrintBasic</d:Types>  
         <CustomMetadata netsted="true">  
            <NestedMetadata>This is a nested custom metadata.</NestedMetadata>  
         </CustomMetadata>  
      </extensions>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 行為也可以用來加入用戶端用來搜尋服務的範圍和類型。 下列範例示範如何在用戶端組態檔中執行這項操作。  
  
```xml  
<behavior name="ep2Behavior">  
   <endpointDiscovery enabled="true">  
      <scopes>  
         <add scope="http://www.microsoft.com/building42/floor1"/>  
         <add scope="ldap:///ou=engineeringo=examplecomc=us"/>  
      </scopes>  
      <types>  
         <add name="test" namespace="http://example.microsoft.com/" />  
         <add name="additionalContract" namespace="http://example.microsoft.com/" />  
      </types>  
   </endpointDiscovery>  
</behavior>  
```  
  
 如需有關<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>和<xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>看到[WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)。  
  
## <a name="binding-element-configuration"></a>繫結項目組態  
 繫結項目組態是用戶端上最有趣的一部分。 您可以使用組態指定尋找準則，用來從 WCF 用戶端應用程式探索服務。  下列範例會建立使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 通道的自訂繫結，並指定包含型別和範圍的尋找準則。 此外，還會指定 <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 和 <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 屬性的值。  
  
```xml  
<bindings>  
   <customBinding>  
      <!-- Binding Configuration for the Application Endpoint -->  
      <binding name="discoBindingConfiguration">  
         <discoveryClient>  
            <endpoint kind="discoveryEndpoint"  
                      address="http://localhost:8000/ConfigTest/Discovery"  
                      binding="customBinding"  
                      bindingConfiguration="httpSoap12WSAddressing10"/>  
            <findCriteria duration="00:00:10" maxResults="2">  
              <types>  
                <add name="IHelloWorldService"/>  
              </types>  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>              
            </findCriteria>  
          </discoveryClient>  
          <textMessageEncoding messageVersion="Soap11"/>  
          <httpTransport />  
        </binding>  
```  
  
 用戶端端點必須參考此自訂繫結組態：  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 如需有關尋找準則，請參閱[探索尋找與尋找準則](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md)。 如需有關探索和繫結項目，請參閱 < [WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>標準端點組態  
 標準端點是預先定義的端點，其中包含一個或多個屬性 (位址、繫結或合約) 的預設值，或是不可變更的一個或多個屬性值。 .NET 4 隨附 3 個探索相關的標準端點：<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>、<xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> 和 <xref:System.ServiceModel.Discovery.DynamicEndpoint>。  <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 是為透過 UDP 多點傳送繫結的探索作業而預先設定的標準端點。 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> 是為透過 UDP 繫結傳送公告訊息而預先設定的標準端點。 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 是在執行階段使用探索動態尋找已探索服務之端點位址的標準端點。  標準繫結會使用 <`endpoint`> 項目指定，該項目中包含指定要加入之標準端點類型的某種屬性。 下列範例示範如何加入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 和 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>。  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->          
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>  
```  
  
 標準端點會在 <`standardEndpoints`> 項目中設定。 下列範例示範如何設定 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 和 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>。  
  
```xml  
<standardEndpoints>  
      <udpAnnouncementEndpoint>  
        <standardEndpoint   
            name="udpAnnouncementEndpointSettings"   
            multicastAddress="soap.udp://239.255.255.250:3703"    
            maxAnnouncementDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="1028"  
            maxPendingMessageCount="10"  
            maxMulticastRetransmitCount="3"  
            maxUnicastRetransmitCount="2"  
            socketReceiveBufferSize="131072"  
            timeToLive="2" />  
        </standardEndpoint>  
      </udpAnnouncementEndpoint>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
            name="udpDiscoveryEndpointSettings"  
            multicastAddress="soap.udp://239.255.255.252:3704"  
            maxResponseDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="2048"  
            maxPendingMessageCount="5"  
            maxReceivedMessageSize="8192"  
            maxBufferPoolSize="262144"/>  
        </standardEndpoint>  
      </udpDiscoveryEndpoint>  
```  
  
 加入標準端點組態之後，請在各端點的 <`endpoint`> 項目中參考該組態，如下列範例所示。  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->          
      <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="udpDiscoveryEndpointSettings"/>  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" endpointConfiguration="udpAnnouncementEndpointSettings" >  
   </service>  
</services>  
```  
  
 與探索中使用的其他標準端點不同的是，您會指定 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 的繫結和合約。 下列範例示範如何加入和設定 <xref:System.ServiceModel.Discovery.DynamicEndpoint>。  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint kind="dynamicEndpoint" binding="basicHttpBinding" contract="IHelloWorldService" endpointConfiguration="dynamicEndpointConfiguration" />  
    </client>   
   <standardEndpoints>  
      <dynamicEndpoint>  
         <standardEndpoint name="dynamicEndpointConfiguration">  
             <discoveryClientSettings>  
              <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="2">  
                 <types>  
                   <add name="IHelloWorldService"/>  
                 </types>  
                 <scopes>  
                   <add scope="http://www.microsoft.com/building42/floor1"/>  
                 </scopes>  
                 <extensions>  
                   <CustomMetadata>This is custom metadata.</CustomMetadata>          
                 </extensions>  
               </findCriteria>  
             </discoveryClientSettings>  
           </standardEndpoint>  
         </dynamicEndpoint>  
   </standardEndpoints>  
</system.ServiceModel>  
```  
  
 如需標準端點的詳細資訊，請參閱[標準端點](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
