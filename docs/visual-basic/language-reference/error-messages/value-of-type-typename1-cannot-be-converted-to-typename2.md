---
title: 類型 '<typename1>' 的值無法轉換成 '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: f6b35efbc445887c537b94dd299b317a28e5f689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406556"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="7142d-102">類型 '\<typename1>' 的值無法轉換成 '\<typename2>'</span><span class="sxs-lookup"><span data-stu-id="7142d-102">Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>
<span data-ttu-id="7142d-103">類型 ' ' 的值 \<typename1> 無法轉換成 ' \<typename2> '。</span><span class="sxs-lookup"><span data-stu-id="7142d-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="7142d-104">類型不符的原因可能是混合了檔案參考與元件 ' ' 的專案參考 \<assemblyname> 。</span><span class="sxs-lookup"><span data-stu-id="7142d-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="7142d-105">請嘗試將專案 ' ' 中 ' ' 的檔案參考取代為 \<filepath> \<projectname1> ' ' 的專案參考 \<projectname2> 。</span><span class="sxs-lookup"><span data-stu-id="7142d-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="7142d-106">在專案同時做為專案參考和檔案參考的情況下，編譯器無法保證一個型別可以轉換成另一個類型。</span><span class="sxs-lookup"><span data-stu-id="7142d-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="7142d-107">下列虛擬程式碼說明可能會產生此錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="7142d-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
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
  
 <span data-ttu-id="7142d-108">Project `P1` 會透過專案對專案進行間接專案參考 `P2` `P3` ，同時也會直接參考的檔案 `P3` 。</span><span class="sxs-lookup"><span data-stu-id="7142d-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="7142d-109">的宣告會 `commonObject` 使用的檔案參考 `P3` ，而呼叫會 `P2.getCommonClass` 使用的專案參考 `P3` 。</span><span class="sxs-lookup"><span data-stu-id="7142d-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="7142d-110">這種情況的問題在於，檔案參考指定了（通常是 p3）輸出檔的檔案路徑和名稱 `P3` ，而專案參考則是依專案名稱識別來源專案（ `P3` ）。</span><span class="sxs-lookup"><span data-stu-id="7142d-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="7142d-111">因此，編譯器無法保證類型會 `P3.commonClass` 透過兩個不同的參考來自相同的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="7142d-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="7142d-112">當專案參考和檔案參考混合時，通常就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="7142d-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="7142d-113">在上圖中，如果 `P1` 直接進行專案參考，而不是檔案參考，就不會發生此問題 `P3` 。</span><span class="sxs-lookup"><span data-stu-id="7142d-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="7142d-114">**錯誤識別碼：** BC30955</span><span class="sxs-lookup"><span data-stu-id="7142d-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7142d-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7142d-115">To correct this error</span></span>  
  
- <span data-ttu-id="7142d-116">將檔案參考變更為專案參考。</span><span class="sxs-lookup"><span data-stu-id="7142d-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7142d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7142d-117">See also</span></span>

- [<span data-ttu-id="7142d-118">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="7142d-118">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="7142d-119">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="7142d-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
