---
title: "將 .NET Framework 元件公開給 COM | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "COM Interop, 公開 COM 元件"
  - "將 .NET Framework 元件公開給 COM"
  - "與 Unmanaged 程式碼的互通, 公開 .NET Framework 元件"
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 將 .NET Framework 元件公開給 COM
撰寫 .NET 型別和從 Unmanaged 程式碼使用該型別，對於開發者而言是明顯不同的活動。  這個章節將描述撰寫與 COM 用戶端互通之 Managed 程式碼的一些秘訣：  
  
-   [限定互通的 .NET 型別](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
  
     所有您要公開給 COM 的 Managed 型別、方法、屬性、欄位和事件都必須是公用的 \(Public\)。  型別必須有公用的預設建構函式 \(Constructor\)，是唯一可以經由 COM 叫用的建構函式。  
  
-   [套用 Interop 屬性](../../../docs/framework/interop/applying-interop-attributes.md)  
  
     在 Managed 程式碼中自訂屬性可以增強元件的互通性 \(Interoperability\)。  
  
-   [封裝 COM 的組件](../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
  
     COM 開發者可能會要求您摘要參考和部署您的組件所涉及的步驟。  
  
 此外，這個章節也指出一些從 COM 用戶端使用 Managed 型別的相關工作。  
  
#### 若要從 COM 使用 Managed 型別  
  
1.  [向 COM 註冊組件](../../../docs/framework/interop/registering-assemblies-with-com.md)  
  
     在組件 \(和型別程式庫\) 中的型別必須在設計階段註冊。  如果安裝程式沒有註冊這個組件，請指示 COM 開發者使用 Regasm.exe。  
  
2.  [參考 COM 的 .NET 型別](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)  
  
     COM 開發者可以使用他們目前使用的相同工具和技術，來參考組件中的型別。  
  
3.  [呼叫 .NET 物件](http://msdn.microsoft.com/zh-tw/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
  
     COM 開發者可以使用他們呼叫任何 Unmanaged 型別上方法的同樣方式，來呼叫 .NET 物件上的方法。  例如，COM **CoCreateInstance** API 會啟動 .NET 物件。  
  
4.  [部署供 COM 存取的應用程式](http://msdn.microsoft.com/zh-tw/fb63564c-c1b9-4655-a094-a235625882ce)。  
  
     強式名稱的組件可以安裝在全域組件快取中，並且需要其發行者的簽章。  沒有強式名稱的組件必須安裝在用戶端的應用程式目錄中。  
  
## 請參閱  
 [與 Unmanaged 程式碼互通](../../../docs/framework/interop/index.md)   
 [COM Interop 範例：COM 用戶端與 .NET 伺服器](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)