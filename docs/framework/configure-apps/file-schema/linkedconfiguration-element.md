---
title: "&lt;linkedConfiguration&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<linkedConfiguration> 項目"
  - "組態檔 [.NET Framework], 連結的組態檔"
  - "包含組態檔"
  - "連結的組態檔"
  - "linkedConfiguration 項目"
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;linkedConfiguration&gt; 項目
指定要包含的組態檔。  
  
## 語法  
  
```  
<linkedConfiguration  
   href="URL of linked configuration file"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`href`|要包含之組態檔的 URL。  `href` 屬性只支援格式 "file:\/\/"。  本機檔案和 UNC 檔案有受到支援。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<assemblyBinding\> 項目](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)|指定位於組態層級的組件繫結原則。|  
  
## 備註  
 `<linkedConfiguration>` 項目會簡化元件組件的服務。  如果一或多個應用程式使用具有組態檔的組件，而該組態檔位於已知位置，則使用該組件之應用程式的組態檔可以使用 `<linkedConfiguration>` 項目來包含該組件的組態檔，而不需直接包含組態資訊。  當元件組件受到服務時，更新一般組態檔會對所有使用該組件的應用程式提供更新的組態資訊。  
  
> [!NOTE]
>  具有 Windows 並存資訊清單的應用程式不支援 `<linkedConfiguration>` 項目。  
  
 下列規則會管理連結之組態檔的使用。  
  
-   包含之組態檔內的設定只會影響到載入器的繫結原則，並且只由載入器使用。  包含的組態檔可以有繫結原則以外的設定，但是這些設定不會產生任何作用。  
  
-   `href` 屬性只支援格式 "file:\/\/"。  本機檔案和 UNC 檔案有受到支援。  
  
-   每個組態檔可連結的組態數目不受限制。  
  
-   所有連結的組態檔會合併為一個檔案，類似於 C\/C\+\+ 內 `#include` 指示詞的行為。  
  
-   `<linkedConfiguration>` 項目只能在應用程式組態檔內使用，在 Machine.config 內會忽略此項目。  
  
-   偵測循環參考，並讓它結束。  也就是說，如果一系列組態檔的 `<linkedConfiguration>` 項目形成迴圈 \(Loop\)，則會偵測該迴圈並停止該迴圈。  
  
## 範例  
 下列程式碼範例說明如何包含本機硬碟的組態檔。  
  
```  
<configuration>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>  
   </assemblyBinding>  
</configuration>  
```  
  
## 請參閱  
 [\<assemblyBinding\> 項目](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
 [組態檔結構描述](../../../../docs/framework/configure-apps/file-schema/index.md)