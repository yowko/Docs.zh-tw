---
title: 開放原始碼程式庫指導
description: 協助開發人員建立高品質 .NET 程式庫的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 50fb745f7eb65abcaca76cebaf9991c48f559e59
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374888"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="4f90f-103">開放原始碼程式庫指導</span><span class="sxs-lookup"><span data-stu-id="4f90f-103">Open-source library guidance</span></span>

<span data-ttu-id="4f90f-104">這份指導提供協助開發人員建立高品質 .NET 程式庫的最佳做法建議。</span><span class="sxs-lookup"><span data-stu-id="4f90f-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="4f90f-105">本文件的重點在於建置 .NET 程式庫時的「內容」與「原因」，而不是「方法」。</span><span class="sxs-lookup"><span data-stu-id="4f90f-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="4f90f-106">高品質開放原始碼 .NET 程式庫的各個層面：</span><span class="sxs-lookup"><span data-stu-id="4f90f-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="4f90f-107">**包山包海** - 優質的 .NET 程式庫致力於支援多種平台與應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f90f-107">**Inclusive** - Good .NET libraries strive to support many platforms and applications.</span></span>
> * <span data-ttu-id="4f90f-108">**穩定可靠** - 優質的 .NET 程式庫可在 .NET 生態環境中共存，能在使用多種程式庫建置而成的應用程式中執行。</span><span class="sxs-lookup"><span data-stu-id="4f90f-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="4f90f-109">**具備演進能力** - .NET 程式庫應該要隨著時間改善與演進，同時支援現有的使用者。</span><span class="sxs-lookup"><span data-stu-id="4f90f-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="4f90f-110">**可供偵錯** - .NET 程式庫應使用最新工具來為使用者打造良好的偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="4f90f-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="4f90f-111">**值得信賴** - .NET 程式庫使用安全性最佳做法來發行到 NuGet，以獲得開發人員的信任。</span><span class="sxs-lookup"><span data-stu-id="4f90f-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4f90f-112">開始使用</span><span class="sxs-lookup"><span data-stu-id="4f90f-112">Get Started</span></span>](./get-started.md)

## <a name="recommendations"></a><span data-ttu-id="4f90f-113">建議</span><span class="sxs-lookup"><span data-stu-id="4f90f-113">Recommendations</span></span>

<span data-ttu-id="4f90f-114">每篇文章都會有一份 .NET 程式庫的建議清單，內含**優先**、**考慮**、**避免**和**禁止**的建議。</span><span class="sxs-lookup"><span data-stu-id="4f90f-114">With each article, there is a list of recommendations for your .NET library using **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="4f90f-115">各項建議的措辭便指出了是否應遵循的程度。</span><span class="sxs-lookup"><span data-stu-id="4f90f-115">The wording of each recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="4f90f-116">**優先**建議是在多數情況下應一律遵循的建議：</span><span class="sxs-lookup"><span data-stu-id="4f90f-116">A **Do** recommendation is one that should almost always be followed:</span></span>

<span data-ttu-id="4f90f-117">**✔️ 優先**使用 NuGet 套件散發您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="4f90f-117">**✔️ DO** distribute your library using a NuGet package.</span></span>

<span data-ttu-id="4f90f-118">至於**考慮**建議則通常應該遵循，但也會有不符合規則的例外，而您不必因為沒有遵循指導而感到自責：</span><span class="sxs-lookup"><span data-stu-id="4f90f-118">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="4f90f-119">**✔️ 考慮**使用 [SemVer 2.0.0](https://semver.org/) 來設定 NuGet 套件的版本。</span><span class="sxs-lookup"><span data-stu-id="4f90f-119">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="4f90f-120">**避免**建議是通常不建議採行的建議，但有時違反規則尚屬合理情況：</span><span class="sxs-lookup"><span data-stu-id="4f90f-120">**Avoid** recommendations are things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="4f90f-121">**❌ 避免**要求明確版本的 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="4f90f-121">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="4f90f-122">最後，**禁止**表示在多數情況下都不應採取的動作：</span><span class="sxs-lookup"><span data-stu-id="4f90f-122">And finally, **do not** indicates something you should almost never do:</span></span>

<span data-ttu-id="4f90f-123">**❌ 禁止**發行程式庫的強式名稱和非強式名稱版本。</span><span class="sxs-lookup"><span data-stu-id="4f90f-123">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="4f90f-124">例如，`Contoso.Api` 和 `Contoso.Api.StrongNamed`。</span><span class="sxs-lookup"><span data-stu-id="4f90f-124">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="4f90f-125">下一步</span><span class="sxs-lookup"><span data-stu-id="4f90f-125">Next</span></span>](./get-started.md)
