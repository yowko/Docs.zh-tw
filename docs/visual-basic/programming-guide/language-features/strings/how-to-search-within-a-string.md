---
title: 如何：在字串內搜尋
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 655f746e4e496e1935afcd2a9f9fe36d9e3a2564
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348416"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="df9f7-102">如何：在字串內搜尋（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="df9f7-102">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="df9f7-103">本文說明如何在 Visual Basic 中的字串內搜尋的範例。</span><span class="sxs-lookup"><span data-stu-id="df9f7-103">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="df9f7-104">範例</span><span class="sxs-lookup"><span data-stu-id="df9f7-104">Example</span></span>

<span data-ttu-id="df9f7-105">這個範例會在 <xref:System.String> 物件上呼叫 <xref:System.String.IndexOf%2A> 方法，以報告子字串第一次出現的索引：</span><span class="sxs-lookup"><span data-stu-id="df9f7-105">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="df9f7-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="df9f7-106">Robust programming</span></span>

<span data-ttu-id="df9f7-107"><xref:System.String.IndexOf%2A> 方法會傳回子字串第一次出現之第一個字元的位置。</span><span class="sxs-lookup"><span data-stu-id="df9f7-107">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="df9f7-108">索引是以0為基礎，表示字串的第一個字元的索引為0。</span><span class="sxs-lookup"><span data-stu-id="df9f7-108">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="df9f7-109">如果 <xref:System.String.IndexOf%2A> 找不到子字串，則會傳回-1。</span><span class="sxs-lookup"><span data-stu-id="df9f7-109">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="df9f7-110"><xref:System.String.IndexOf%2A> 方法會區分大小寫，而且會使用目前的文化特性。</span><span class="sxs-lookup"><span data-stu-id="df9f7-110">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="df9f7-111">若要獲得最佳錯誤控制，您可以將字串搜尋放在 Try 的 `Try` 區塊中 ... [Catch .。。Finally 語句](../../../language-reference/statements/try-catch-finally-statement.md)結構。</span><span class="sxs-lookup"><span data-stu-id="df9f7-111">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="df9f7-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="df9f7-112">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="df9f7-113">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="df9f7-113">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="df9f7-114">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="df9f7-114">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="df9f7-115">字串</span><span class="sxs-lookup"><span data-stu-id="df9f7-115">Strings</span></span>](index.md)
