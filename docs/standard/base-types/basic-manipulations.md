---
title: .NET 中的基底字元串操作
description: 請參閱呼叫許多字串方法的範例。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: cc04f0c874b732668b4813f8325bd7060927f22a
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889123"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>如何：在 .NET 中執行基本字串操作

下列範例會使用[基本字串作業](basic-string-operations.md)主題中所討論的一些方法，以一種可能在實際應用程式中發現的方式，來建構可執行字串操作的類別。 `MailToData` 類別會將個人的姓名和地址儲存在不同的屬性中，並允許您將 `City`、`State` 和 `Zip` 欄位組合成單一字串，以便顯示給使用者看。 此外，類別也可讓使用者將城市、省/市和郵遞區號當成單一字串來輸入；應用程式會自動剖析這個單一字串，然後將正確的資訊輸入對應的屬性中。  
  
為了簡單起見，這個範例會使用具有命令列介面的主控台應用程式。  
  
## <a name="example"></a>範例  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
執行上述程式碼時，系統會要求使用者輸入其名稱和位址。 應用程式會將這項資訊放入適當的屬性中，並建立出顯示城市、省/市和郵遞區號資訊的單一字串，將資訊重新顯示給使用者看。  
  
## <a name="see-also"></a>請參閱

- [基底字元串作業](basic-string-operations.md)
