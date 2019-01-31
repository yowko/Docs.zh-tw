---
title: HOW TO：卸載應用程式定義域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42356348ba454ffe0c3778e23dc9a0ff272c9f64
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727738"
---
# <a name="how-to-unload-an-application-domain"></a>HOW TO：卸載應用程式定義域
當您完成使用應用程式定義域時，請使用 <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> 方法將它卸載。 **Unload** 方法會依正常程序關閉指定的應用程式定義域。 在卸載過程中，任何新的執行緒皆不得存取應用程式定義域，且系統會將所有應用程式定義域特定的資料結構釋放出來，  
  
 並將已載入應用程式定義域的組件移除，而不再可供使用。 如果應用程式定義域中的組件為定義域中性組件，則系統會將組件的資料保留在記憶體中，直到整個程序關閉為止。 目前沒有任何機制可以卸載定義域中性的組件，因此您只能關閉整個程序。 有時候，卸載應用程式定義域的要求可能無法運作，並會導致 <xref:System.CannotUnloadAppDomainException>。  
  
 下列範例會建立名為 `MyDomain` 的新應用程式定義域，再將部分資訊列印到主控台中，然後卸載應用程式定義域。 請注意，此時程式碼會嘗試將已卸載之應用程式定義域的易記名稱列印至主控台。 這個動作會產生一個例外狀況，並由程式結尾的 try/catch 陳述式進行處理。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>另請參閱
- [使用應用程式定義域設計程式](application-domains.md#programming-with-application-domains)
- [如何：建立應用程式定義域](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)
- [使用應用程式定義域](../../../docs/framework/app-domains/use.md)
