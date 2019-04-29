---
title: 類型 '<typename1>' 的值無法轉換成 '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 5f313a43bc3a2f983dabbd45477d120fdb80d063
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766801"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="ec7a5-102">類型的值 '\<typename1 >' 無法轉換成'\<2&gt >'</span><span class="sxs-lookup"><span data-stu-id="ec7a5-102">Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>
<span data-ttu-id="ec7a5-103">類型的值 '\<typename1 >' 無法轉換成'\<2&gt >'。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="ec7a5-104">型別不相符可能是因為混用了檔案參考和組件的專案參考的 '\<組件名稱 >'。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="ec7a5-105">請嘗試更換的檔案參考 '\<檔案路徑 >' 在專案'\<projectname1 >' 的專案參考 '\<專案名稱 2> >'。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="ec7a5-106">其中一個專案可專案參考和檔案參考的情況下，編譯器無法保證一個類型可轉換成另一個。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="ec7a5-107">下列虛擬程式碼說明可能會產生此錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
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
  
 <span data-ttu-id="ec7a5-108">專案`P1`會透過專案間接的專案參考`P2`專案`P3`，和也直接與檔案參考`P3`。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="ec7a5-109">宣告`commonObject`使用的檔案參考`P3`，而呼叫`P2.getCommonClass`使用的專案參考`P3`。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="ec7a5-110">在此情況下問題就是檔案參考指定的檔案路徑與名稱的輸出檔案`P3`(通常 p3.dll)，在專案參考中找到的原始碼專案時 (`P3`) 依專案名稱。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="ec7a5-111">因此，編譯器無法保證類型`P3.commonClass`來自相同的原始程式碼，透過兩個不同的參考。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="ec7a5-112">通常會發生這種情況在混合的檔案參考和專案的參考時。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="ec7a5-113">在上圖中，就不會發生問題如果`P1`所做的直接存取的專案參考`P3`而非檔案參考。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="ec7a5-114">**錯誤 ID:** BC30955</span><span class="sxs-lookup"><span data-stu-id="ec7a5-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ec7a5-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ec7a5-115">To correct this error</span></span>  
  
- <span data-ttu-id="ec7a5-116">變更的專案參考的檔案參考。</span><span class="sxs-lookup"><span data-stu-id="ec7a5-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec7a5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec7a5-117">See also</span></span>

- [<span data-ttu-id="ec7a5-118">在 Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="ec7a5-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="ec7a5-119">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="ec7a5-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
