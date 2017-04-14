---
title: "限定互通的 .NET 類型 | Microsoft Docs"
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
  - "COM Interop, 限定 .NET 類型"
  - "將 .NET Framework 元件公開給 COM"
  - "與 Unmanaged 程式碼的互通, 公開 .NET Framework 元件"
  - "與 Unmanaged 程式碼的互通, 限定 .NET 類型"
  - "限定互通的 .NET 類型"
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 限定互通的 .NET 類型
如果您打算將組件中的型別公開給 COM 應用程式，請在設計階段考慮 COM Interop 的需求。  如果您嚴格遵守以下的方針，就可以緊密地整合 Managed 型別 \(類別、介面、結構和列舉\) 和 COM 型別：  
  
-   類別應該明確地實作介面  
  
     雖然 COM Interop 提供了一種機制，會自動產生含有類別之所有成員及其基底類別 \(Base Class\) 成員的介面，不過最好還是提供明確的介面。  自動產生的介面稱為類別介面。  如需相關方針，請參閱[類別介面簡介](http://msdn.microsoft.com/zh-tw/733c0dd2-12e5-46e6-8de1-39d5b25df024)。  
  
     您可以使用 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C\# 和 C\+\+，將介面定義加入程式碼中，而不必使用介面定義語言 \(IDL\) 或其他相等的語言。  如需語法的詳細資訊，請參閱您的程式語言文件。  
  
-   Managed 型別必須為公用  
  
     只有組件中的公用型別會註冊及匯出至型別程式庫。  因此，COM 只能看得見公用型別。  
  
     Managed 型別公開給其他 Managed 程式碼的功能不一定會公開給 COM。  例如，參數型建構函式、靜態方法及常數欄位，都不會公開給 COM 用戶端。  此外，當 Runtime 封送處理資料進出型別時，這些資料可能會被複製或轉換。  
  
-   方法、屬性、欄位和事件必須為公用  
  
     公用型別的成員如果要讓 COM 看到的話，它們也必須是公用。  您可以套用 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 來限制組件、公用型別或公用型別之公用成員的可視性。  根據預設，所以公用型別和成員都是可以看見的。  
  
-   型別必須具有要從 COM 啟動的公用預設建構函式  
  
     COM 可以看得見 Managed 公用型別。  但是，如果沒有公用預設建構函式 \(一種沒有引數的建構函式\)，COM 用戶端就不能建立這個型別。  如果 COM 用戶端是用其他方式啟動的，它仍然可以使用型別。  
  
-   型別不可為抽象的  
  
     COM 用戶端或 .NET 用戶端都不可以建立抽象型別。  
  
 當匯出至 COM 時，Managed 型別的繼承階層架構 \(Inheritance Hierarchy\) 會扁平化。  而且 Managed 和 Unmanaged 環境之間的版本也會不同。  公開給 COM 的型別與其他 Managed 型別各有不同的版本特性。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 [將 .NET Framework 元件公開給 COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [Introducing the Class Interface](http://msdn.microsoft.com/zh-tw/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [套用 Interop 屬性](../../../docs/framework/interop/applying-interop-attributes.md)   
 [封裝 COM 的組件](../../../docs/framework/interop/packaging-an-assembly-for-com.md)