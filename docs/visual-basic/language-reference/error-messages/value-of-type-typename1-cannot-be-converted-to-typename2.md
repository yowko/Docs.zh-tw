---
title: "類型的值 &quot;&lt;typename1&gt;&quot;無法轉換成&quot;&lt;typename2&gt;&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
dev_langs:
- VB
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
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
ms.openlocfilehash: 2fbe1550515d2b15a3e349392fc8d78812787ae4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a><span data-ttu-id="f5be7-102">類型的值 '&lt;typename1&gt;'無法轉換成'&lt;typename2&gt;'</span><span class="sxs-lookup"><span data-stu-id="f5be7-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="f5be7-103">類型的值 '\<typename1 >' 無法轉換成'\<typename2 >'。</span><span class="sxs-lookup"><span data-stu-id="f5be7-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="f5be7-104">型別不相符可能是因為混用了檔案參考和組件的專案參考 '\<assemblyname >'。</span><span class="sxs-lookup"><span data-stu-id="f5be7-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="f5be7-105">請嘗試更換檔案參考 '\<filepath >' 在專案中'\<projectname1 >' 的專案參考 '\<projectname2 >'。</span><span class="sxs-lookup"><span data-stu-id="f5be7-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="f5be7-106">專案參考和檔案參考專案可讓的情況下，編譯器無法保證，可以轉換成另一種類型。</span><span class="sxs-lookup"><span data-stu-id="f5be7-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="f5be7-107">下列虛擬程式碼將說明可能產生此錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="f5be7-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 <span data-ttu-id="f5be7-108">專案`P1`會透過專案間接專案參考`P2`專案`P3`，以及也直接檔案參考`P3`。</span><span class="sxs-lookup"><span data-stu-id="f5be7-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="f5be7-109">宣告`commonObject`使用的檔案參考`P3`，而呼叫`P2.getCommonClass`會使用專案參考`P3`。</span><span class="sxs-lookup"><span data-stu-id="f5be7-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="f5be7-110">這種情況的問題是檔案參考指定檔案路徑和名稱的輸出檔`P3`(通常 p3.dll)，在專案參考中找到原始碼專案時 (`P3`) 的專案名稱。</span><span class="sxs-lookup"><span data-stu-id="f5be7-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="f5be7-111">因此，編譯器無法保證類型`P3.commonClass`來自相同的原始程式碼，透過兩個不同的參考。</span><span class="sxs-lookup"><span data-stu-id="f5be7-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="f5be7-112">通常發生這種情況在混合檔案參考和專案的參考時。</span><span class="sxs-lookup"><span data-stu-id="f5be7-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="f5be7-113">在上圖中，問題就不會發生如果`P1`所做的直接專案參考`P3`而非檔案參考。</span><span class="sxs-lookup"><span data-stu-id="f5be7-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="f5be7-114">**錯誤識別碼︰** BC30955</span><span class="sxs-lookup"><span data-stu-id="f5be7-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5be7-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f5be7-115">To correct this error</span></span>  
  
-   <span data-ttu-id="f5be7-116">變更專案參考的檔案參考。</span><span class="sxs-lookup"><span data-stu-id="f5be7-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5be7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5be7-117">See Also</span></span>  
 <span data-ttu-id="f5be7-118">[在 Visual Basic 中的型別轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="f5be7-118">[Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="f5be7-119"> [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="f5be7-119"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="f5be7-120"> [NIB 如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span><span class="sxs-lookup"><span data-stu-id="f5be7-120"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span></span>
