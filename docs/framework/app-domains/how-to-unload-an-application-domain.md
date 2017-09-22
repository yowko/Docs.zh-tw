---
title: "如何：卸載應用程式定義域"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eefaf670202e6b4977d75fffa906f1b07053eb3e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：卸載應用程式定義域
當您結束應用程式定義域的使用時，可以使用 [System.AppDomain.Unload](frlrfSystemAppDomainClassUnloadTopic) 方法將之卸載。  **Unload** 方法可以順利關閉指定的應用程式定義域。  在卸載處理序期間，新的執行緒將無法存取應用程式定義域，而且所有應用程式定義域特定的資料結構都將釋放出來。  
  
 已載入至應用程式定義域的組件會被移除，並且無法再使用。  如果應用程式定義域中的組件是定義域中性的，那麼除非整個處理序都已關閉，否則組件的資料會保留在記憶體中。  卸載定義域中性組件的唯一機制便是關閉整個處理序。  有時候卸載應用程式定義域的要求並不會成功，而且會產生 <xref:System.CannotUnloadAppDomainException>。  
  
 下列範例建立新的應用程式定義域 \(名為 `MyDomain`\) 將某些資訊列印到主控台後，再卸載應用程式定義域。  請注意，接下來程式碼將嘗試列印卸載應用程式定義域的名稱到主控台。  這個動作將會在程式結束時產生一則由 Try\/Catch 陳述式處理的例外狀況。  
  
## 範例  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## 請參閱  
 [Programming with Application Domains](http://msdn.microsoft.com/zh-tw/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [如何：建立應用程式定義域](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)   
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)

