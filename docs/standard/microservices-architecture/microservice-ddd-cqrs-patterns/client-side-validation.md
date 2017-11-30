---
title: "用戶端驗證 （驗證在介面層級）"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |用戶端驗證 （驗證在介面層級）"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: db88a3b5c95afdc8d5a20094105f1f5991483ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="b7371-104">用戶端驗證 （驗證在介面層級）</span><span class="sxs-lookup"><span data-stu-id="b7371-104">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="b7371-105">即使事實來源是網域模型，最後您必須擁有網域模型層級的驗證，驗證仍可處理的網域模型層級 （伺服器端） 和用戶端。</span><span class="sxs-lookup"><span data-stu-id="b7371-105">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the client side.</span></span>

<span data-ttu-id="b7371-106">用戶端驗證是絕佳方便使用者。</span><span class="sxs-lookup"><span data-stu-id="b7371-106">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="b7371-107">它會將儲存它們要否則花的時間等候來回行程可能會傳回驗證錯誤的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b7371-107">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="b7371-108">中的商務詞彙表示，即使是幾個句號乘以達數百次每一天加總很多的時間、 支出和挫折度中。</span><span class="sxs-lookup"><span data-stu-id="b7371-108">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="b7371-109">直接和立即驗證可讓使用者更有效率地運作，並產生較佳的品質，輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="b7371-109">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="b7371-110">就如同檢視模型和網域模型都不同，檢視模型的驗證和網域模型驗證可能類似，但有不同用途。</span><span class="sxs-lookup"><span data-stu-id="b7371-110">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="b7371-111">如果您擔心有關乾 （不重複自行原則），請考慮在此情況下重複使用程式碼也可能表示結合，，和企業應用程式中是不並結合至遵循乾原則比對用戶端的伺服器端更重要。</span><span class="sxs-lookup"><span data-stu-id="b7371-111">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="b7371-112">即使在使用用戶端驗證，您應該一律驗證您的命令或輸入 DTOs 伺服端程式碼，因為伺服器應用程式開發介面是可能的攻擊媒介。</span><span class="sxs-lookup"><span data-stu-id="b7371-112">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="b7371-113">通常，同時是最好的選擇，所以如果您的用戶端應用程式，UX 的觀點而言，最好是主動式，而且不允許使用者輸入無效的資訊。</span><span class="sxs-lookup"><span data-stu-id="b7371-113">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="b7371-114">因此，在用戶端程式碼中您通常驗證 ViewModels。</span><span class="sxs-lookup"><span data-stu-id="b7371-114">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="b7371-115">您也無法驗證用戶端輸出 DTOs 或命令，然後再傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="b7371-115">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="b7371-116">用戶端驗證的實作取決於您要建立何種用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7371-116">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="b7371-117">它將會不同如果您要驗證 web MVC web 應用程式中的資料與大多數的程式碼，在.NET 中，以驗證正在 JavaScript 或 TypeScript，請在自動程式化 SPA web 應用程式或行動裝置應用程式自動程式碼使用 Xamarin 和 C\#。</span><span class="sxs-lookup"><span data-stu-id="b7371-117">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C\#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b7371-118">其他資源</span><span class="sxs-lookup"><span data-stu-id="b7371-118">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="b7371-119">Xamarin 的行動裝置應用程式的驗證</span><span class="sxs-lookup"><span data-stu-id="b7371-119">Validation in Xamarin mobile apps</span></span>

-   <span data-ttu-id="b7371-120">**驗證文字輸入和顯示錯誤**
    [*https://developer.xamarin.com/recipes/ios/standard\_控制項] / [文字\_欄位/驗證\_輸入 /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span><span class="sxs-lookup"><span data-stu-id="b7371-120">**Validate Text Input and Show Errors**
[*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span></span>

-   <span data-ttu-id="b7371-121">**驗證回呼**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span><span class="sxs-lookup"><span data-stu-id="b7371-121">**Validation Callback**
[*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span></span>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="b7371-122">ASP.NET Core 應用程式中的驗證</span><span class="sxs-lookup"><span data-stu-id="b7371-122">Validation in ASP.NET Core apps</span></span>

-   <span data-ttu-id="b7371-123">**Rick Anderson，加入驗證**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="b7371-123">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="b7371-124">SPA 中的驗證 Web 應用程式 (角度 2，TypeScript，JavaScript)</span><span class="sxs-lookup"><span data-stu-id="b7371-124">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

-   <span data-ttu-id="b7371-125">**Ado Kukic。角度 2 表單驗證** **
     ** [ *https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span><span class="sxs-lookup"><span data-stu-id="b7371-125">**Ado Kukic. Angular 2 Form Validation** **
**[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span></span>

-   <span data-ttu-id="b7371-126">**表單驗證**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span><span class="sxs-lookup"><span data-stu-id="b7371-126">**Form Validation**
[*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span></span>

-   <span data-ttu-id="b7371-127">**驗證。**</span><span class="sxs-lookup"><span data-stu-id="b7371-127">**Validation.**</span></span> <span data-ttu-id="b7371-128">幫助您輕鬆文件。</span><span class="sxs-lookup"><span data-stu-id="b7371-128">Breeze documentation.</span></span>
    [<span data-ttu-id="b7371-129">*http://breeze.github.io/doc-js/validation.html*</span><span class="sxs-lookup"><span data-stu-id="b7371-129">*http://breeze.github.io/doc-js/validation.html*</span></span>](http://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="b7371-130">在 [摘要] 中，這些是對於驗證而言最重要的概念：</span><span class="sxs-lookup"><span data-stu-id="b7371-130">In summary, these are the most important concepts in regards to validation:</span></span>

-   <span data-ttu-id="b7371-131">實體和彙總應該強制執行它們自己的一致性，以及 「 永遠有效 」。</span><span class="sxs-lookup"><span data-stu-id="b7371-131">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="b7371-132">彙總根負責內相同的彙總的多實體一致性。</span><span class="sxs-lookup"><span data-stu-id="b7371-132">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

-   <span data-ttu-id="b7371-133">如果您認為，實體必須輸入無效的狀態，請考慮使用不同的物件模型，例如，使用暫存 DTO，直到您建立的最後一個網域實體。</span><span class="sxs-lookup"><span data-stu-id="b7371-133">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

-   <span data-ttu-id="b7371-134">如果您需要建立數個相關的物件，例如彙總，但它們只有效全部都建立之後，請考慮使用處理站模式。</span><span class="sxs-lookup"><span data-stu-id="b7371-134">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

-   <span data-ttu-id="b7371-135">驗證架構是最適合用在特定層級，例如展示層或應用程式/服務層，但通常不在網域模型層級，因為您必須依賴強式基礎結構架構。</span><span class="sxs-lookup"><span data-stu-id="b7371-135">Validation frameworks are best used in specific layers, such as the presentation layer or the application/service layer, but usually not in the domain model layer, because you would need to take a strong dependency on an infrastructure framework.</span></span>

-   <span data-ttu-id="b7371-136">在許多情況下，重複驗證在用戶端相當好的因為應用程式可主動。</span><span class="sxs-lookup"><span data-stu-id="b7371-136">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b7371-137">[上一個](網域-模式-圖層-validations.md) [下一步] (網域-事件-設計-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="b7371-137">[Previous] (domain-model-layer-validations.md) [Next] (domain-events-design-implementation.md)</span></span>
