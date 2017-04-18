---
title: "&lt;tokenReplayCache&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;tokenReplayCache&gt;
語彙基元重新顯示快取使用註冊的服務或安全性語彙基元的處理常式集合。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|type|型別衍生自<xref:System.IdentityModel.Tokens.TokenReplayCache>類別。  如需有關如何指定自訂的`type`，請參閱[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。|  
  
### 子項目  
 None  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<caches\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|註冊服務或安全性語彙基元的處理常式集合所使用的快取。|  
  
## 備註  
 語彙基元重新顯示快取用來偵測重新執行的語彙基元。  語彙基元重新執行偵測啟用的[\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)項目，也會指定語彙基元的最大的到期時間。  
  
## 範例  
 下列 XML 程式碼會顯示自訂的快取來偵測重新執行的語彙基元的設定。  
  
```  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>   
 [\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)