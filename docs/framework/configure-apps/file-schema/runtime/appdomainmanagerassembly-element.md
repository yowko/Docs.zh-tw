---
title: "&lt;appDomainManagerAssembly&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<appDomainManagerAssembly> 項目"
  - "appDomainManagerAssembly 項目"
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;appDomainManagerAssembly&gt; 項目
指定在處理序中為預設應用程式定義域提供應用程式定義域管理員的組件。  
  
## 語法  
  
```  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`value`|必要屬性。  指定在處理序中為預設應用程式定義域提供應用程式定義域管理員的組件顯示名稱。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 若要指定應用程式定義域管理員的型別，您必須同時指定這個項目及 [\<appDomainManagerType\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) 項目。  如果兩個項目中有任一個未指定，就會忽略另一個已指定的項目。  
  
 載入預設應用程式定義域之後，如果指定的組件不存在或不含 [\<appDomainManagerType\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) 項目指定的型別，就會擲回 <xref:System.TypeLoadException>，而處理序也無法啟動。  如果有指定的組件，但是版本資訊不相符，則會擲回 <xref:System.IO.FileLoadException>。  
  
 當您指定預設應用程式定義域的應用程式定義域管理員型別時，從預設應用程式定義域建立的其他應用程式定義域都會繼承應用程式定義域管理員型別。  您可以使用 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=fullName> 和 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=fullName> 屬性，為新的應用程式定義域指定不同的應用程式定義域管理員型別。  
  
 應用程式必須具有完全信任權限，才能指定應用程式定義域管理員型別 \(例如，在桌面上執行的應用程式具有完全信任權限\)。如果應用程式沒有完全信任權限，就會擲回 <xref:System.TypeLoadException>。  
  
 如需組件顯示名稱格式的詳細描述，請參閱 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=fullName> 屬性 \(Property\)。  
  
 這個組態項目只能在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] \(含\) 以後版本中使用。  
  
## 範例  
 下列範例示範如何將處理序之預設應用程式定義域的應用程式定義域管理員指定為 `AdMgrExample` 組件中的 `MyMgr` 型別。  
  
```  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=fullName>   
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=fullName>   
 [\<appDomainManagerType\> 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)   
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [SetAppDomainManagerType 方法](../Topic/ICLRControl::SetAppDomainManagerType%20Method.md)