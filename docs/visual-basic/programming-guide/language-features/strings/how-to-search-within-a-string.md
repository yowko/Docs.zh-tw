---
title: 如何：在字串內搜尋-Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700067"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>如何：在字串內搜尋（Visual Basic）

本文說明如何在 Visual Basic 中的字串內搜尋的範例。

## <a name="example"></a>範例

這個範例會在 @no__t 1 物件上呼叫 <xref:System.String.IndexOf%2A> 方法，以報告子字串第一次出現的索引：

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>穩固程式設計

@No__t-0 方法會傳回子字串第一次出現之第一個字元的位置。 索引是以0為基礎，表示字串的第一個字元的索引為0。

如果 <xref:System.String.IndexOf%2A> 找不到子字串，則會傳回-1。

@No__t-0 方法會區分大小寫，而且會使用目前的文化特性。

若要獲得最佳錯誤控制，您可以將字串搜尋放在 Try 的 `Try` 區塊中 ... [Catch .。。Finally 語句](../../../language-reference/statements/try-catch-finally-statement.md)結構。

## <a name="see-also"></a>另請參閱

- <xref:System.String.IndexOf%2A>
- [Try...Catch...Finally 陳述式](../../../language-reference/statements/try-catch-finally-statement.md)
- [Visual Basic 中的字串簡介](introduction-to-strings.md)
- [字串](index.md)
