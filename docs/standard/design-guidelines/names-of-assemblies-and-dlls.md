---
title: "組件和 Dll 的名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "名稱 [.NET Framework] Dll"
  - "名稱 [.NET Framework] 組件"
  - "組件 [.NET Framework] 名稱"
  - "Dll 名稱"
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 組件和 Dll 的名稱
組件是部署和 managed 程式碼程式的身分識別的單位。 雖然組件可以跨越一或多個檔案，通常對應一對一的 DLL 組件。 因此，本章節描述唯一 DLL 的命名慣例，然後可以對應至組件命名慣例。  
  
 **✓ 執行** 選擇建議的功能，例如 System.Data 大型區塊的 Dll 組件的名稱。  
  
 組件和 DLL 的名稱不一定要對應至命名空間名稱，但很合理的組件命名時，請依照下列命名空間名稱。 好的經驗法則是名稱的組件中所包含的組件的一般前置詞為基礎的 DLL。 例如，兩個命名空間，將組件 `MyCompany.MyTechnology.FirstFeature` 和 `MyCompany.MyTechnology.SecondFeature`, ，可能會呼叫 `MyCompany.MyTechnology.dll`。  
  
 **✓ 考慮** 命名 Dll 根據下列模式︰  
  
 `<Company>.<Component>.dll`  
  
 其中 `<Component>` 包含一個或多個點分隔的子句。 例如：  
  
 `Litware.Controls.dll`.  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)