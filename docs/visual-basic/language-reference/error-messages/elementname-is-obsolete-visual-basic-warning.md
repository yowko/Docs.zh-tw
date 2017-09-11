---
title: "&quot;&lt;elementname&gt;&quot; 已過時 （Visual Basic 警告） |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
dev_langs:
- VB
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 77708f052f7aec7a5da2b24605ba3bd794f83979
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a><span data-ttu-id="48eb0-102">'&lt;elementname&gt;' 已過時 （Visual Basic 警告）</span><span class="sxs-lookup"><span data-stu-id="48eb0-102">&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="48eb0-103">陳述式嘗試存取程式設計的項目被標示與<xref:System.ObsoleteAttribute>屬性並將其視為警告指示詞。</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="48eb0-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="48eb0-104">您可以將標記為不再使用<xref:System.ObsoleteAttribute>該</xref:System.ObsoleteAttribute>套用任何程式設計項目</span><span class="sxs-lookup"><span data-stu-id="48eb0-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="48eb0-105">如果您這麼做，您可以設定屬性的<xref:System.ObsoleteAttribute.IsError%2A>屬性設為`True`或`False`。</xref:System.ObsoleteAttribute.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="48eb0-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="48eb0-106">如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="48eb0-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="48eb0-107">如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="48eb0-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="48eb0-108">根據預設，這是一個警告訊息，因為<xref:System.ObsoleteAttribute.IsError%2A>屬性<xref:System.ObsoleteAttribute>是`False`。</xref:System.ObsoleteAttribute> </xref:System.ObsoleteAttribute.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="48eb0-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="48eb0-109">如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="48eb0-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="48eb0-110">**錯誤識別碼︰** BC40008</span><span class="sxs-lookup"><span data-stu-id="48eb0-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="48eb0-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="48eb0-111">To correct this error</span></span>  
  
-   <span data-ttu-id="48eb0-112">確定原始程式碼參考正確拼寫項目名稱。</span><span class="sxs-lookup"><span data-stu-id="48eb0-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48eb0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48eb0-113">See Also</span></span>  
 [<span data-ttu-id="48eb0-114">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="48eb0-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

