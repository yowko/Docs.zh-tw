---
ms.openlocfilehash: 1805c26f1eff46719f30de8a14ca6d35f01948a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234666"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a><span data-ttu-id="9e1b2-101">Foreach 迭代器變數的範圍現在會設定為在反覆項目內，因此關閉擷取語意不同 (在 C#5 中)</span><span class="sxs-lookup"><span data-stu-id="9e1b2-101">Foreach iterator variable is now scoped within the iteration, so closure capturing semantics are different (in C#5)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9e1b2-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e1b2-102">Details</span></span>|<span data-ttu-id="9e1b2-103">從 C# 5 (Visual Studio 2012) 開始，<code>foreach</code> 迭代器變數的範圍會設定為在反覆項目內。</span><span class="sxs-lookup"><span data-stu-id="9e1b2-103">Beginning with C# 5 (Visual Studio 2012), <code>foreach</code> iterator variables are scoped within the iteration.</span></span> <span data-ttu-id="9e1b2-104">如果程式碼之前需要這些變數才不會包含在 <code>foreach</code> 的關閉中，這可能會導致中斷。</span><span class="sxs-lookup"><span data-stu-id="9e1b2-104">This can cause breaks if code was previously depending on the variables to not be included in the <code>foreach</code>'s closure.</span></span> <span data-ttu-id="9e1b2-105">這項變更的徵兆是傳遞至委派的迭代器變數會視為建立委派時所具有的值，而不是叫用委派時所具有的值。</span><span class="sxs-lookup"><span data-stu-id="9e1b2-105">The symptom of this change is that an iterator variable passed to a delegate is treated as the value it has at the time the delegate is created, rather than the value it has at the time the delegate is invoked.</span></span>|
|<span data-ttu-id="9e1b2-106">建議</span><span class="sxs-lookup"><span data-stu-id="9e1b2-106">Suggestion</span></span>|<span data-ttu-id="9e1b2-107">在理想情況下，您應該更新程式碼，以確保此新的編譯器行為。</span><span class="sxs-lookup"><span data-stu-id="9e1b2-107">Ideally, code should be updated to expect the new compiler behavior.</span></span> <span data-ttu-id="9e1b2-108">如果需要舊版語意，您可以將此迭代器變數取代成明確放在迴圈範圍外的不同變數。</span><span class="sxs-lookup"><span data-stu-id="9e1b2-108">If the old semantics are required, the iterator variable can be replaced with a separate variable which is explicitly placed outside of the loop's scope.</span></span>|
|<span data-ttu-id="9e1b2-109">範圍</span><span class="sxs-lookup"><span data-stu-id="9e1b2-109">Scope</span></span>|<span data-ttu-id="9e1b2-110">主要</span><span class="sxs-lookup"><span data-stu-id="9e1b2-110">Major</span></span>|
|<span data-ttu-id="9e1b2-111">版本</span><span class="sxs-lookup"><span data-stu-id="9e1b2-111">Version</span></span>|<span data-ttu-id="9e1b2-112">4.5</span><span class="sxs-lookup"><span data-stu-id="9e1b2-112">4.5</span></span>|
|<span data-ttu-id="9e1b2-113">類型</span><span class="sxs-lookup"><span data-stu-id="9e1b2-113">Type</span></span>|<span data-ttu-id="9e1b2-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="9e1b2-114">Retargeting</span></span>|
