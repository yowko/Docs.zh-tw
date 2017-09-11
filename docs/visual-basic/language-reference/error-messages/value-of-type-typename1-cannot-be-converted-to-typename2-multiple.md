---
title: "類型的值 &quot;&lt;typename1&gt;&quot;無法轉換成&quot;&lt;typename2&gt;&quot; （多重檔案參考） |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
dev_langs:
- VB
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: 9
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
ms.openlocfilehash: 299cc4bec00a4597a661c5da49135fe3b5357537
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="d66ea-102">類型的值 '&lt;typename1&gt;'無法轉換成'&lt;typename2&gt;' （多重檔案參考）</span><span class="sxs-lookup"><span data-stu-id="d66ea-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="d66ea-103">類型的值 '\<typename1 >' 無法轉換成'\<typename2 >'。</span><span class="sxs-lookup"><span data-stu-id="d66ea-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="d66ea-104">型別不相符可能是因為混用的檔案參考 '\<filepath1 >' 在專案中'\<projectname1 >' 的檔案參考 '\<filepath2 >' 在專案中'\<projectname2 >'。</span><span class="sxs-lookup"><span data-stu-id="d66ea-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="d66ea-105">如果兩個組件相同，請嘗試更換這些參考，讓兩個參考都來自相同的位置。</span><span class="sxs-lookup"><span data-stu-id="d66ea-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="d66ea-106">其中一個專案可讓多個檔案參考的組件的情況下，編譯器無法保證，可以轉換成另一種類型。</span><span class="sxs-lookup"><span data-stu-id="d66ea-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="d66ea-107">每個檔案參考指定檔案路徑和名稱 （通常是 DLL 檔案） 專案的輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="d66ea-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="d66ea-108">編譯器無法保證輸出檔，來自相同的來源，或其所代表的同一組件相同的版本。</span><span class="sxs-lookup"><span data-stu-id="d66ea-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="d66ea-109">因此，它無法保證在不同的參考型別都相同的型別，或其中甚至可以轉換成其他。</span><span class="sxs-lookup"><span data-stu-id="d66ea-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="d66ea-110">如果您知道參考的組件具有相同的組件識別，您可以使用單一檔案參考。</span><span class="sxs-lookup"><span data-stu-id="d66ea-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="d66ea-111">*「組件識別」* (assembly identity) 包含組件的名稱、版本、公開金鑰 (如果有) 和文化特性。</span><span class="sxs-lookup"><span data-stu-id="d66ea-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="d66ea-112">這是可唯一識別組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="d66ea-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="d66ea-113">**錯誤識別碼︰** BC30961</span><span class="sxs-lookup"><span data-stu-id="d66ea-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d66ea-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d66ea-114">To correct this error</span></span>  
  
-   <span data-ttu-id="d66ea-115">如果參考的組件具有相同的組件識別，然後移除或取代其中一個檔案參考，讓它只包含單一檔案的參考。</span><span class="sxs-lookup"><span data-stu-id="d66ea-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="d66ea-116">如果參考的組件不具有相同的組件識別，請變更您的程式碼，使它不會轉換成其他類型的其中一個型別。</span><span class="sxs-lookup"><span data-stu-id="d66ea-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d66ea-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d66ea-117">See Also</span></span>  
 <span data-ttu-id="d66ea-118">[在 Visual Basic 中的型別轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="d66ea-118">[Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="d66ea-119"> [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="d66ea-119"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="d66ea-120"> [NIB 如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span><span class="sxs-lookup"><span data-stu-id="d66ea-120"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span></span>
