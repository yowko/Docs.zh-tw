---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617139"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a><span data-ttu-id="807cd-101">Foreach 迭代器變數的範圍現在會設定為在反覆項目內，因此關閉擷取語意不同 (在 C#5 中)</span><span class="sxs-lookup"><span data-stu-id="807cd-101">Foreach iterator variable is now scoped within the iteration, so closure capturing semantics are different (in C#5)</span></span>

#### <a name="details"></a><span data-ttu-id="807cd-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="807cd-102">Details</span></span>

<span data-ttu-id="807cd-103">從 C# 5 (Visual Studio 2012) 開始，`foreach` 迭代器變數的範圍會設定為在反覆項目內。</span><span class="sxs-lookup"><span data-stu-id="807cd-103">Beginning with C# 5 (Visual Studio 2012), `foreach` iterator variables are scoped within the iteration.</span></span> <span data-ttu-id="807cd-104">如果程式碼之前需要這些變數才不會包含在 `foreach` 的關閉中，這可能會導致中斷。</span><span class="sxs-lookup"><span data-stu-id="807cd-104">This can cause breaks if code was previously depending on the variables to not be included in the `foreach`'s closure.</span></span> <span data-ttu-id="807cd-105">這項變更的徵兆是傳遞至委派的迭代器變數會視為建立委派時所具有的值，而不是叫用委派時所具有的值。</span><span class="sxs-lookup"><span data-stu-id="807cd-105">The symptom of this change is that an iterator variable passed to a delegate is treated as the value it has at the time the delegate is created, rather than the value it has at the time the delegate is invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="807cd-106">建議</span><span class="sxs-lookup"><span data-stu-id="807cd-106">Suggestion</span></span>

<span data-ttu-id="807cd-107">在理想情況下，您應該更新程式碼，以確保此新的編譯器行為。</span><span class="sxs-lookup"><span data-stu-id="807cd-107">Ideally, code should be updated to expect the new compiler behavior.</span></span> <span data-ttu-id="807cd-108">如果需要舊版語意，您可以將此迭代器變數取代成明確放在迴圈範圍外的不同變數。</span><span class="sxs-lookup"><span data-stu-id="807cd-108">If the old semantics are required, the iterator variable can be replaced with a separate variable which is explicitly placed outside of the loop's scope.</span></span>

| <span data-ttu-id="807cd-109">名稱</span><span class="sxs-lookup"><span data-stu-id="807cd-109">Name</span></span>    | <span data-ttu-id="807cd-110">值</span><span class="sxs-lookup"><span data-stu-id="807cd-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="807cd-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="807cd-111">Scope</span></span>   | <span data-ttu-id="807cd-112">主要</span><span class="sxs-lookup"><span data-stu-id="807cd-112">Major</span></span>       |
| <span data-ttu-id="807cd-113">版本</span><span class="sxs-lookup"><span data-stu-id="807cd-113">Version</span></span> | <span data-ttu-id="807cd-114">4.5</span><span class="sxs-lookup"><span data-stu-id="807cd-114">4.5</span></span>         |
| <span data-ttu-id="807cd-115">類型</span><span class="sxs-lookup"><span data-stu-id="807cd-115">Type</span></span>    | <span data-ttu-id="807cd-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="807cd-116">Retargeting</span></span> |
