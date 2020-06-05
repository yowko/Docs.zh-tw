---
title: 類型 '<typename1>' 的值無法轉換成 '<typename2>' (多重檔案參考)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 25008f05979638e050b74fc659fdc0a6d13b3c31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406582"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="5f89d-102">類型 '\<typename1>' 的值無法轉換成 '\<typename2>' (多重檔案參考)</span><span class="sxs-lookup"><span data-stu-id="5f89d-102">Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>
<span data-ttu-id="5f89d-103">類型 ' ' 的值 \<typename1> 無法轉換成 ' \<typename2> '。</span><span class="sxs-lookup"><span data-stu-id="5f89d-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="5f89d-104">類型不符的原因可能是因為在專案 ' ' 中混用 ' ' 的檔案參考 \<filepath1> \<projectname1> 與 \<filepath2> 專案 ' ' 中 ' ' 的檔案參考 \<projectname2> 。</span><span class="sxs-lookup"><span data-stu-id="5f89d-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="5f89d-105">如果兩個組件相同，請嘗試更換這些參考，讓兩個參考都來自相同的位置。</span><span class="sxs-lookup"><span data-stu-id="5f89d-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="5f89d-106">在專案對元件進行多個檔案參考的情況下，編譯器無法保證一個類型可以轉換成另一個。</span><span class="sxs-lookup"><span data-stu-id="5f89d-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="5f89d-107">每個檔案參考都會指定專案輸出檔的檔案路徑和名稱（通常是 DLL 檔案）。</span><span class="sxs-lookup"><span data-stu-id="5f89d-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="5f89d-108">編譯器無法保證輸出檔案來自相同的來源，或其代表相同元件的相同版本。</span><span class="sxs-lookup"><span data-stu-id="5f89d-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="5f89d-109">因此，它無法保證不同參考中的類型都是相同的類型，甚至是可以轉換成另一個。</span><span class="sxs-lookup"><span data-stu-id="5f89d-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="5f89d-110">如果您知道參考的元件具有相同的元件識別，您可以使用單一檔案參考。</span><span class="sxs-lookup"><span data-stu-id="5f89d-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="5f89d-111">*元件識別*包含元件的名稱、版本、公開金鑰（如果有）和文化特性。</span><span class="sxs-lookup"><span data-stu-id="5f89d-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="5f89d-112">這是可唯一識別組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="5f89d-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="5f89d-113">**錯誤識別碼：** BC30961</span><span class="sxs-lookup"><span data-stu-id="5f89d-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5f89d-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5f89d-114">To correct this error</span></span>  
  
- <span data-ttu-id="5f89d-115">如果參考的元件具有相同的元件識別，則請移除或取代其中一個檔案參考，讓只有一個檔案參考。</span><span class="sxs-lookup"><span data-stu-id="5f89d-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
- <span data-ttu-id="5f89d-116">如果參考的元件不具有相同的元件識別，請變更您的程式碼，使其不會嘗試將某個類型轉換成另一個中的類型。</span><span class="sxs-lookup"><span data-stu-id="5f89d-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f89d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f89d-117">See also</span></span>

- [<span data-ttu-id="5f89d-118">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="5f89d-118">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="5f89d-119">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="5f89d-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
