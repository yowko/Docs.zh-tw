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
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>用戶端驗證 （驗證在介面層級）

即使事實來源是網域模型，最後您必須擁有網域模型層級的驗證，驗證仍可處理的網域模型層級 （伺服器端） 和用戶端。

用戶端驗證是絕佳方便使用者。 它會將儲存它們要否則花的時間等候來回行程可能會傳回驗證錯誤的伺服器。 中的商務詞彙表示，即使是幾個句號乘以達數百次每一天加總很多的時間、 支出和挫折度中。 直接和立即驗證可讓使用者更有效率地運作，並產生較佳的品質，輸入和輸出。

就如同檢視模型和網域模型都不同，檢視模型的驗證和網域模型驗證可能類似，但有不同用途。 如果您擔心有關乾 （不重複自行原則），請考慮在此情況下重複使用程式碼也可能表示結合，，和企業應用程式中是不並結合至遵循乾原則比對用戶端的伺服器端更重要。

即使在使用用戶端驗證，您應該一律驗證您的命令或輸入 DTOs 伺服端程式碼，因為伺服器應用程式開發介面是可能的攻擊媒介。 通常，同時是最好的選擇，所以如果您的用戶端應用程式，UX 的觀點而言，最好是主動式，而且不允許使用者輸入無效的資訊。

因此，在用戶端程式碼中您通常驗證 ViewModels。 您也無法驗證用戶端輸出 DTOs 或命令，然後再傳送至服務。

用戶端驗證的實作取決於您要建立何種用戶端應用程式。 它將會不同如果您要驗證 web MVC web 應用程式中的資料與大多數的程式碼，在.NET 中，以驗證正在 JavaScript 或 TypeScript，請在自動程式化 SPA web 應用程式或行動裝置應用程式自動程式碼使用 Xamarin 和 C\#。

## <a name="additional-resources"></a>其他資源

### <a name="validation-in-xamarin-mobile-apps"></a>Xamarin 的行動裝置應用程式的驗證

-   **驗證文字輸入和顯示錯誤**
    [*https://developer.xamarin.com/recipes/ios/standard\_控制項] / [文字\_欄位/驗證\_輸入 /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **驗證回呼**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>ASP.NET Core 應用程式中的驗證

-   **Rick Anderson，加入驗證**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>SPA 中的驗證 Web 應用程式 (角度 2，TypeScript，JavaScript)

-   **Ado Kukic。角度 2 表單驗證** **
     ** [ *https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **表單驗證**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **驗證。** 幫助您輕鬆文件。
    [*http://breeze.github.io/doc-js/validation.html*](http://breeze.github.io/doc-js/validation.html)

在 [摘要] 中，這些是對於驗證而言最重要的概念：

-   實體和彙總應該強制執行它們自己的一致性，以及 「 永遠有效 」。 彙總根負責內相同的彙總的多實體一致性。

-   如果您認為，實體必須輸入無效的狀態，請考慮使用不同的物件模型，例如，使用暫存 DTO，直到您建立的最後一個網域實體。

-   如果您需要建立數個相關的物件，例如彙總，但它們只有效全部都建立之後，請考慮使用處理站模式。

-   驗證架構是最適合用在特定層級，例如展示層或應用程式/服務層，但通常不在網域模型層級，因為您必須依賴強式基礎結構架構。

-   在許多情況下，重複驗證在用戶端相當好的因為應用程式可主動。


>[!div class="step-by-step"]
[上一個](網域-模式-圖層-validations.md) [下一步] (網域-事件-設計-implementation.md)
