---
title: "&lt;configuration&gt; 的 &lt;assemblyBinding&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<assemblyBinding> 項目"
  - "assemblyBinding 項目"
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;configuration&gt; 的 &lt;assemblyBinding&gt; 項目
指定位於組態層級的組件繫結原則。  
  
## 語法  
  
```  
<assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1">  
</assemblyBinding>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`xmlns`|必要屬性。<br /><br /> 指定組件繫結所需要的 XML 命名空間 \(Namespace\)。  使用字串 "urn:schemas\-microsoft\-com:asm.v1" 做為該值。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<linkedConfiguration\> 項目](../../../../docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)|指定要包含的組態檔。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<configuration\> 項目](../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## 備註  
 [\<linkedConfiguration\> 項目](../../../../docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) 藉由讓應用程式組態檔包含位於已知位置的組件組態檔，而不是採用複製組件組態設定的方式，以簡化元件組件的管理程序。  
  
> [!NOTE]
>  具有 Windows 並存資訊清單的應用程式不支援 `<linkedConfiguration>` 項目。  
  
## 範例  
 下列程式碼範例說明如何在本機硬碟上包含組態檔。  
  
```  
<configuration>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>  
   </assemblyBinding>  
</configuration>  
```  
  
## 請參閱  
 [組態檔結構描述](../../../../docs/framework/configure-apps/file-schema/index.md)