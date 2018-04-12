---
title: '&lt;type1&gt;&#39;&lt;typename&gt;&#39; 必須實作 &#39;&lt;membername&gt;&#39; 介面 &#39;&lt;介面名稱&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05e0229d0259c519d4db265c017a5040b425c79a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="addaa-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; 必須實作 &#39;&lt;membername&gt;&#39; 介面 &#39;&lt;介面名稱&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="addaa-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="addaa-103">'\<類型名稱 >' 必須實作'\<成員名稱 >' 的介面 '\<介面名稱 >'。</span><span class="sxs-lookup"><span data-stu-id="addaa-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="addaa-104">實作屬性必須有相符的 'ReadOnly '/' WriteOnly' 規範。</span><span class="sxs-lookup"><span data-stu-id="addaa-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="addaa-105">類別或結構實作介面宣告，但未實作程序、 屬性或介面所定義的事件。</span><span class="sxs-lookup"><span data-stu-id="addaa-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="addaa-106">必須實作介面的每個成員。</span><span class="sxs-lookup"><span data-stu-id="addaa-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="addaa-107">**錯誤 ID:** BC30154</span><span class="sxs-lookup"><span data-stu-id="addaa-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="addaa-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="addaa-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="addaa-109">宣告具有相同名稱和簽章的介面中所定義的成員。</span><span class="sxs-lookup"><span data-stu-id="addaa-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="addaa-110">務必包含最少為`End Function`， `End Sub`，或`End Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="addaa-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="addaa-111">新增`Implements`子句結尾`Function`， `Sub`， `Property`，或`Event`陳述式。</span><span class="sxs-lookup"><span data-stu-id="addaa-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="addaa-112">例如：</span><span class="sxs-lookup"><span data-stu-id="addaa-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="addaa-113">當實作屬性，請確定`ReadOnly`或`WriteOnly`介面定義的相同方式中使用。</span><span class="sxs-lookup"><span data-stu-id="addaa-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="addaa-114">當實作屬性，宣告`Get`和`Set`程序，視需要。</span><span class="sxs-lookup"><span data-stu-id="addaa-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="addaa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="addaa-115">See Also</span></span>  
 [<span data-ttu-id="addaa-116">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="addaa-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="addaa-117">介面</span><span class="sxs-lookup"><span data-stu-id="addaa-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
