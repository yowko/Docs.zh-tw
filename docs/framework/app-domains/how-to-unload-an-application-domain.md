---
title: "如何：卸載應用程式定義域 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b9146d7565809cc0f92556478f93b9d444538826
ms.contentlocale: zh-tw
ms.lasthandoff: 06/02/2017

---
<a id="how-to-unload-an-application-domain" class="xliff"></a>

# 如何：卸載應用程式定義域
當您完成使用應用程式定義域時，請使用 <xref:System.AppDomain.Unload%2A?displayProperty=fullName> 方法將它卸載。 **Unload** 方法會依正常程序關閉指定的應用程式定義域。 在卸載過程中，任何新的執行緒皆不得存取應用程式定義域，且系統會將所有應用程式定義域特定的資料結構釋放出來，  
  
 並將已載入應用程式定義域的組件移除，而不再可供使用。 如果應用程式定義域中的組件為定義域中性組件，則系統會將組件的資料保留在記憶體中，直到整個程序關閉為止。 目前沒有任何機制可以卸載定義域中性的組件，因此您只能關閉整個程序。 有時候，卸載應用程式定義域的要求可能無法運作，並會導致 <xref:System.CannotUnloadAppDomainException>。  
  
 下列範例會建立名為 `MyDomain` 的新應用程式定義域，再將部分資訊列印到主控台中，然後卸載應用程式定義域。 請注意，此時程式碼會嘗試將已卸載之應用程式定義域的易記名稱列印至主控台。 這個動作會產生一個例外狀況，並由程式結尾的 try/catch 陳述式進行處理。  
  
<a id="example" class="xliff"></a>

## 範例  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)] [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)] [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
<a id="see-also" class="xliff"></a>

## 另請參閱  
 [使用應用程式定義域設計程式](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [如何：建立應用程式定義域](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)   
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)
