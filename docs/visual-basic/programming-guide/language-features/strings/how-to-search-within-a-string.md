---
title: "如何：在字串內搜尋 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c828d0b32fdf90e121e9d5da0bb60ab11c212f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="d5356-102">如何：在字串內搜尋 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5356-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="d5356-103">這個範例會呼叫<xref:System.String.IndexOf%2A>方法<xref:System.String>来報告的第一個子字串索引的物件。</span><span class="sxs-lookup"><span data-stu-id="d5356-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5356-104">範例</span><span class="sxs-lookup"><span data-stu-id="d5356-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d5356-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d5356-105">Compiling the Code</span></span>  
 <span data-ttu-id="d5356-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d5356-106">This example requires:</span></span>  
  
-   <span data-ttu-id="d5356-107">`Imports`陳述式指定<xref:System>命名空間。</span><span class="sxs-lookup"><span data-stu-id="d5356-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="d5356-108">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="d5356-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d5356-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="d5356-109">Robust Programming</span></span>  
 <span data-ttu-id="d5356-110"><xref:System.String.IndexOf%2A>方法會回報第一個子字串的第一個字元的位置。</span><span class="sxs-lookup"><span data-stu-id="d5356-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="d5356-111">索引是以 0 為基礎，這表示字串的第一個字元索引為 0。</span><span class="sxs-lookup"><span data-stu-id="d5356-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="d5356-112">如果<xref:System.String.IndexOf%2A>找不到子字串，則傳回-1。</span><span class="sxs-lookup"><span data-stu-id="d5356-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="d5356-113"><xref:System.String.IndexOf%2A>方法會區分大小寫，而且會使用目前文化特性。</span><span class="sxs-lookup"><span data-stu-id="d5356-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="d5356-114">您可能要括住的字串搜尋，在最佳錯誤控制項`Try`區塊[再試一次...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)建構。</span><span class="sxs-lookup"><span data-stu-id="d5356-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5356-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5356-115">See Also</span></span>  
 <xref:System.String.IndexOf%2A>  
 [<span data-ttu-id="d5356-116">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="d5356-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="d5356-117">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="d5356-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="d5356-118">字串</span><span class="sxs-lookup"><span data-stu-id="d5356-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
