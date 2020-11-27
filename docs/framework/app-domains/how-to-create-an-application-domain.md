---
title: 作法：建立應用程式定義域
description: 複習如何在 .NET 中建立應用程式域。 您可以建立應用程式域來載入元件以管理個人，或建立一個應用程式域來執行程式碼。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: fb022511ee395a9312e4dbaf7c0beee03c9b4569
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264084"
---
# <a name="how-to-create-an-application-domain"></a>作法：建立應用程式定義域

Common Language Runtime Host 會在有需要時自動建立應用程式定義域。 不過，您可以建立自己的應用程式定義域，將它們載入您想要自行管理的組件中。 您也可以建立要從中執行程式碼的應用程式定義域。  
  
 使用 <xref:System.AppDomain?displayProperty=nameWithType> 類別的其中一個多載 **CreateDomain** 方法，建立新的應用程式定義域。 您可以提供應用程式定義域的名稱，並依該名稱參考它。  
  
 以下範例會建立新的應用程式定義域並指派名稱 `MyDomain`，然後將主機網域和新建子應用程式定義域的名稱列印至主控台。  
  
## <a name="example"></a>範例  

 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [使用應用程式定義域設計程式](application-domains.md#programming-with-application-domains)
- [使用應用程式定義域](use.md)
