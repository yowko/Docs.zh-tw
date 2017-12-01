---
title: "如何：在 .NET Framework 中執行基本字串操作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee9c00d02b7b5d1f391ce60f843c18445efd6edc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>如何： 在.NET 中執行基本字串操作
下列範例會使用中所討論之方法的部分[基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)主題，以建構可能會發現在真實世界的應用程式的方式來執行字串操作的類別。 `MailToData` 類別會將個人的姓名和地址儲存在不同的屬性中，並允許您將 `City`、`State` 和 `Zip` 欄位組合成單一字串，以便顯示給使用者看。 此外，類別也可讓使用者將城市、省/市和郵遞區號當成單一字串來輸入；應用程式會自動剖析這個單一字串，然後將正確的資訊輸入對應的屬性中。  
  
 為了簡單起見，這個範例會使用具有命令列介面的主控台應用程式。  
  
## <a name="example"></a>範例  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 執行上述程式碼時，會要求使用者輸入自己的姓名和地址。 應用程式會將這項資訊放入適當的屬性中，並建立出顯示城市、省/市和郵遞區號資訊的單一字串，將資訊重新顯示給使用者看。  
  
## <a name="see-also"></a>另請參閱  
 [基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)
