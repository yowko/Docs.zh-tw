---
title: 類型 '<typename1>' 的值無法轉換成 '<typename2>' (多重檔案參考)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 23c051e57014d7479d1c1c522b1a8da1ead52c19
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161383"
---
# <a name="bc30961-value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="76fc9-102">BC30961：類型 ' ' 的值 \<typename1> 無法轉換成 ' \<typename2> ' (多個檔案參考) </span><span class="sxs-lookup"><span data-stu-id="76fc9-102">BC30961: Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>

<span data-ttu-id="76fc9-103">類型 ' ' 的值 \<typename1> 無法轉換成 ' \<typename2> '。</span><span class="sxs-lookup"><span data-stu-id="76fc9-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="76fc9-104">類型不符的原因可能是混合 \<filepath1> 專案 ' ' 中的 ' ' 檔案參考 \<projectname1> 與專案 ' ' 中的 ' \<filepath2> ' 檔案參考 \<projectname2> 。</span><span class="sxs-lookup"><span data-stu-id="76fc9-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="76fc9-105">如果兩個組件相同，請嘗試更換這些參考，讓兩個參考都來自相同的位置。</span><span class="sxs-lookup"><span data-stu-id="76fc9-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>

 <span data-ttu-id="76fc9-106">在專案對元件建立多個檔案參考的情況下，編譯器無法保證可以將一個類型轉換成另一個類型。</span><span class="sxs-lookup"><span data-stu-id="76fc9-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>

 <span data-ttu-id="76fc9-107">每個檔案參考都會指定專案輸出檔的檔案路徑和名稱， (通常是) 的 DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="76fc9-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="76fc9-108">編譯器無法保證輸出檔來自相同的來源，或者它們代表相同元件的相同版本。</span><span class="sxs-lookup"><span data-stu-id="76fc9-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="76fc9-109">因此，它無法保證不同參考中的型別是相同類型，或甚至可以轉換成另一個參考。</span><span class="sxs-lookup"><span data-stu-id="76fc9-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>

 <span data-ttu-id="76fc9-110">如果您知道參考的元件具有相同的元件識別，則可以使用單一檔案參考。</span><span class="sxs-lookup"><span data-stu-id="76fc9-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="76fc9-111">*元件身分識別*包含元件的名稱、版本、公開金鑰（如果有）和文化特性。</span><span class="sxs-lookup"><span data-stu-id="76fc9-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="76fc9-112">這是可唯一識別組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="76fc9-112">This information uniquely identifies the assembly.</span></span>

 <span data-ttu-id="76fc9-113">**錯誤識別碼：** BC30961</span><span class="sxs-lookup"><span data-stu-id="76fc9-113">**Error ID:** BC30961</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="76fc9-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="76fc9-114">To correct this error</span></span>

- <span data-ttu-id="76fc9-115">如果參考的元件具有相同的元件識別，則請移除或取代其中一個檔案參考，如此就只會有單一檔案參考。</span><span class="sxs-lookup"><span data-stu-id="76fc9-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>

- <span data-ttu-id="76fc9-116">如果參考的元件沒有相同的元件識別，則請變更您的程式碼，使其不會嘗試將某個類型轉換成另一個類型。</span><span class="sxs-lookup"><span data-stu-id="76fc9-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>

## <a name="see-also"></a><span data-ttu-id="76fc9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76fc9-117">See also</span></span>

- [<span data-ttu-id="76fc9-118">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="76fc9-118">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="76fc9-119">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="76fc9-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
