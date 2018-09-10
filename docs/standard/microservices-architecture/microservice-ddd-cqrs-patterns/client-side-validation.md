---
title: 用戶端驗證 (展示層中的驗證)
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 用戶端驗證 (展示層中的驗證)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 70a1f716797e03acdcbf1c58d4b0302449d98fa9
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275033"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="225ec-103">用戶端驗證 (展示層中的驗證)</span><span class="sxs-lookup"><span data-stu-id="225ec-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="225ec-104">即使事實來源是領域模型，而且您最終必須有領域模型層級的驗證，驗證仍可在領域模型層級 (伺服器端) 和用戶端處理。</span><span class="sxs-lookup"><span data-stu-id="225ec-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the client side.</span></span>

<span data-ttu-id="225ec-105">用戶端驗證對使用者而言很方便。</span><span class="sxs-lookup"><span data-stu-id="225ec-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="225ec-106">它為使用者省下花在等候可能傳回驗證錯誤之伺服器往返的時間。</span><span class="sxs-lookup"><span data-stu-id="225ec-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="225ec-107">對商務而言，即便是幾秒，若每天乘上好幾百倍，也可能讓您花上許多時間和費用，而倍感挫折。</span><span class="sxs-lookup"><span data-stu-id="225ec-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="225ec-108">直接和立即驗證可讓使用者更有效率地工作，並產生更佳品質的輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="225ec-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="225ec-109">就像是檢視模型與領域模型不同，檢視模型驗證與領域模型驗證可能類似，但目的卻不同。</span><span class="sxs-lookup"><span data-stu-id="225ec-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="225ec-110">如果您擔心 DRY (不重複原則)，請注意在此案例程式碼中，重複使用程式碼也可能表示結合，而在企業應用程式中，不要結合伺服器端與用戶端會比遵循不重複原則更重要。</span><span class="sxs-lookup"><span data-stu-id="225ec-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="225ec-111">即使是使用用戶端驗證，您應該一律在伺服器程式碼中驗證您的命令或輸入 DTO，因為伺服器 API 可能會是攻擊媒介。</span><span class="sxs-lookup"><span data-stu-id="225ec-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="225ec-112">通常，如果您有用戶端應用程式，最好是同時執行，從 UX 的觀點來看，最好是採取主動，而不是讓使用者輸入無效的資訊。</span><span class="sxs-lookup"><span data-stu-id="225ec-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="225ec-113">因此，在用戶端程式碼中，您通常會驗證 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="225ec-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="225ec-114">您也可以驗證用戶端輸出 DTO 或命令，再將它們傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="225ec-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="225ec-115">用戶端驗證的實作取決於您要建置的用戶端應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="225ec-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="225ec-116">如果您想要在大部分程式碼是以 .NET 撰寫的 Web MVC Web 應用程式、具有以 JavaScript 或 TypeScript 所撰寫之驗證的 SPA Web 應用程式，或是以 Xamarin 和 C# 撰寫的行動應用程式中驗證資料，則是不同的情況。</span><span class="sxs-lookup"><span data-stu-id="225ec-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="225ec-117">其他資源</span><span class="sxs-lookup"><span data-stu-id="225ec-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="225ec-118">Xamarin 行動應用程式中的驗證</span><span class="sxs-lookup"><span data-stu-id="225ec-118">Validation in Xamarin mobile apps</span></span>

-   <span data-ttu-id="225ec-119">**驗證文字輸入，並顯示錯誤**
    [*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span><span class="sxs-lookup"><span data-stu-id="225ec-119">**Validate Text Input and Show Errors**
[*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span></span>

-   <span data-ttu-id="225ec-120">**驗證回呼**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span><span class="sxs-lookup"><span data-stu-id="225ec-120">**Validation Callback**
[*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span></span>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="225ec-121">ASP.NET Core 應用程式中的驗證</span><span class="sxs-lookup"><span data-stu-id="225ec-121">Validation in ASP.NET Core apps</span></span>

-   <span data-ttu-id="225ec-122">**Rick Anderson，新增驗證**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="225ec-122">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="225ec-123">SPA Web 應用程式中的驗證 (Angular 2、TypeScript、JavaScript)</span><span class="sxs-lookup"><span data-stu-id="225ec-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

-   <span data-ttu-id="225ec-124">**Ado Kukic：Angular 2 表單驗證**
    [*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span><span class="sxs-lookup"><span data-stu-id="225ec-124">**Ado Kukic. Angular 2 Form Validation**
[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span></span>

-   <span data-ttu-id="225ec-125">\*\*表單驗證 \*\*
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span><span class="sxs-lookup"><span data-stu-id="225ec-125">**Form Validation**
[*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span></span>

-   <span data-ttu-id="225ec-126">**Validation (驗證)，**</span><span class="sxs-lookup"><span data-stu-id="225ec-126">**Validation.**</span></span> <span data-ttu-id="225ec-127">Breeze 文件，</span><span class="sxs-lookup"><span data-stu-id="225ec-127">Breeze documentation.</span></span>
    [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="225ec-128">總而言之，這些是對於驗證而言最重要的概念：</span><span class="sxs-lookup"><span data-stu-id="225ec-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="225ec-129">實體和彙總應該強制執行它們自己的一致性，而且「永遠有效」。</span><span class="sxs-lookup"><span data-stu-id="225ec-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="225ec-130">彙總根目錄負責相同彙總內的多實體一致性。</span><span class="sxs-lookup"><span data-stu-id="225ec-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="225ec-131">如果您認為實體必須進入無效狀態，請考慮使用不同的物件模型；例如，使用暫存 DTO，直到您建立最後一個領域實體。</span><span class="sxs-lookup"><span data-stu-id="225ec-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="225ec-132">如果您需要建立數個相關的物件 (例如彙總)，而且這些物件只有在全部建立之後才有效，請考慮使用 Factory 模式。</span><span class="sxs-lookup"><span data-stu-id="225ec-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="225ec-133">驗證架構是最適合用於特定層級，例如展示層或應用程式/服務層，但通常不適合用於領域模型層，因為您必須強烈依賴基礎結構架構。</span><span class="sxs-lookup"><span data-stu-id="225ec-133">Validation frameworks are best used in specific layers, such as the presentation layer or the application/service layer, but usually not in the domain model layer, because you would need to take a strong dependency on an infrastructure framework.</span></span>

- <span data-ttu-id="225ec-134">在許多情況下，在用戶端重複驗證是不錯的做法，因為應用程式可以採取主動。</span><span class="sxs-lookup"><span data-stu-id="225ec-134">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="225ec-135">[上一頁](domain-model-layer-validations.md)
[下一頁](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="225ec-135">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>