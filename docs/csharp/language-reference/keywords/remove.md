---
title: remove 內容關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 70b324b8bca09701ead398eb6586ad181826e5f4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527227"
---
# <a name="remove-c-reference"></a>remove (C# 參考)

使用 `remove` 內容關鍵字定義自訂事件存取子，以在用戶端程式碼取消訂閱[事件](event.md)時叫用。 如果您提供自訂 `remove` 存取子，則也必須提供 [add](add.md) 存取子。

## <a name="example"></a>範例

下列範例示範具有自訂 [add](add.md) 和 `remove` 存取子的事件。 如需完整範例，請參閱[如何：實作介面事件](../../programming-guide/events/how-to-implement-interface-events.md)。

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

您通常不需要提供自己的自訂事件存取子。 宣告事件時編譯器自動產生的存取子，足以應付大部分的狀況。

## <a name="see-also"></a>另請參閱

- [事件](../../programming-guide/events/index.md)