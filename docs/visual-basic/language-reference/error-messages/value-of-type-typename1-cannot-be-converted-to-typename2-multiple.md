---
title: "類型 &#39; 的值&lt;typename1&gt;&#39; 無法轉換成 &#39;&lt;2>&gt;&#39;（多個檔案參考）"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f22516a5ca9626f43cb89745e67c66619cf9461f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="3b142-102">類型 &#39; 的值&lt;typename1&gt;&#39; 無法轉換成 &#39;&lt;2>&gt;&#39;（多個檔案參考）</span><span class="sxs-lookup"><span data-stu-id="3b142-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="3b142-103">類型的值 '\<typename1 >' 無法轉換成'\<2> >'。</span><span class="sxs-lookup"><span data-stu-id="3b142-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="3b142-104">類型不符的情況可能是因為混用了檔案參考 '\<filepath1 >' 在專案中'\<projectname1 >' 的檔案參考 '\<filepath2 >' 在專案'\<專案名稱 2> >'。</span><span class="sxs-lookup"><span data-stu-id="3b142-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="3b142-105">如果兩個組件相同，請嘗試更換這些參考，讓兩個參考都來自相同的位置。</span><span class="sxs-lookup"><span data-stu-id="3b142-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="3b142-106">專案位置會一個以上的檔案參考的組件的情況下，編譯器無法保證，可以轉換成另一種類型。</span><span class="sxs-lookup"><span data-stu-id="3b142-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="3b142-107">每個檔案參考指定檔案路徑和名稱的專案 （通常是 DLL 檔案） 的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="3b142-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="3b142-108">編譯器無法保證輸出檔，來自相同的來源，或它們代表相同的版本相同組件。</span><span class="sxs-lookup"><span data-stu-id="3b142-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="3b142-109">因此，它無法保證不同的參考中的類型為相同類型，或甚至一可轉換成另。</span><span class="sxs-lookup"><span data-stu-id="3b142-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="3b142-110">如果您知道參考的組件具有相同的組件識別，您可以使用單一檔案參考。</span><span class="sxs-lookup"><span data-stu-id="3b142-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="3b142-111">*「組件識別」* (assembly identity) 包含組件的名稱、版本、公開金鑰 (如果有) 和文化特性。</span><span class="sxs-lookup"><span data-stu-id="3b142-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="3b142-112">這是可唯一識別組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="3b142-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="3b142-113">**錯誤 ID:** BC30961</span><span class="sxs-lookup"><span data-stu-id="3b142-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3b142-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="3b142-114">To correct this error</span></span>  
  
-   <span data-ttu-id="3b142-115">如果參考的組件具有相同的組件識別，然後移除或取代其中一個檔案的參考，以便只包含單一檔案的參考。</span><span class="sxs-lookup"><span data-stu-id="3b142-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="3b142-116">如果參考的組件不會有相同的組件識別，然後變更您的程式碼，使它不會轉換成其他類型的其中一個型別。</span><span class="sxs-lookup"><span data-stu-id="3b142-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b142-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="3b142-117">See Also</span></span>  
 [<span data-ttu-id="3b142-118">在 Visual Basic 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="3b142-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="3b142-119">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="3b142-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 
