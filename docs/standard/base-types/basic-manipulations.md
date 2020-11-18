---
title: .NET 中的基底字元串操作
description: 請參閱呼叫許多字串方法的範例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: e3e969520e068bde234c13d45ad790b76ecf8fdb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825152"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>如何：在 .NET 中執行基本字串操作

下列範例會使用[基本字串作業](basic-string-operations.md)主題中所討論的一些方法，以一種可能在實際應用程式中發現的方式，來建構可執行字串操作的類別。 `MailToData` 類別會將個人的姓名和地址儲存在不同的屬性中，並允許您將 `City`、`State` 和 `Zip` 欄位組合成單一字串，以便顯示給使用者看。 此外，此類別可讓使用者以單一字串形式輸入 city、state 和 zip 程式碼資訊。 應用程式會自動剖析單一字串，並將適當的資訊輸入到對應的屬性中。

為了簡單起見，這個範例會使用具有命令列介面的主控台應用程式。

## <a name="example"></a>範例

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]

執行上述程式碼時，系統會要求使用者輸入其名稱和位址。 應用程式會將資訊放在適當的屬性中，並向使用者顯示資訊，並建立單一字串來顯示城市、州和郵遞區號資訊。

## <a name="see-also"></a>請參閱

- [基底字元串作業](basic-string-operations.md)
