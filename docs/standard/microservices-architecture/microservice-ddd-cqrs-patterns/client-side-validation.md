---
title: 用戶端驗證 (展示層中的驗證)
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 用戶端驗證 (展示層中的驗證)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 2adce39561dd2b97910155ebed595a2df7785c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>用戶端驗證 (展示層中的驗證)

即使事實來源是領域模型，而且您最終必須有領域模型層級的驗證，驗證仍可在領域模型層級 (伺服器端) 和用戶端處理。

用戶端驗證對使用者而言很方便。 它為使用者省下花在等候可能傳回驗證錯誤之伺服器往返的時間。 對商務而言，即便是幾秒，若每天乘上好幾百倍，也可能讓您花上許多時間和費用，而倍感挫折。 直接和立即驗證可讓使用者更有效率地工作，並產生更佳品質的輸入和輸出。

就像是檢視模型與領域模型不同，檢視模型驗證與領域模型驗證可能類似，但目的卻不同。 如果您擔心 DRY (不重複原則)，請注意在此案例程式碼中，重複使用程式碼也可能表示結合，而在企業應用程式中，不要結合伺服器端與用戶端會比遵循不重複原則更重要。

即使是使用用戶端驗證，您應該一律在伺服器程式碼中驗證您的命令或輸入 DTO，因為伺服器 API 可能會是攻擊媒介。 通常，如果您有用戶端應用程式，最好是同時執行，從 UX 的觀點來看，最好是採取主動，而不是讓使用者輸入無效的資訊。

因此，在用戶端程式碼中，您通常會驗證 ViewModel。 您也可以驗證用戶端輸出 DTO 或命令，再將它們傳送至服務。

用戶端驗證的實作取決於您要建置的用戶端應用程式類型。 如果您想要在大部分程式碼是以 .NET 撰寫的 Web MVC Web 應用程式、具有以 JavaScript 或 TypeScript 所撰寫之驗證的 SPA Web 應用程式，或是以 Xamarin 和 C\# 撰寫的行動應用程式中驗證資料，則是不同的情況。

## <a name="additional-resources"></a>其他資源

### <a name="validation-in-xamarin-mobile-apps"></a>Xamarin 行動應用程式中的驗證

-   **驗證文字輸入和顯示錯誤**
    [*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **驗證回呼**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>ASP.NET Core 應用程式中的驗證

-   **Rick Anderson，新增驗證**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>SPA Web 應用程式中的驗證 (Angular 2、TypeScript、JavaScript)

-   **Ado Kukic：Angular 2 表單驗證** **
    **[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **表單驗證 **
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **Validation (驗證)，** Breeze 文件，
    [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

總而言之，這些是對於驗證而言最重要的概念：

-   實體和彙總應該強制執行它們自己的一致性，而且「永遠有效」。 彙總根目錄負責相同彙總內的多實體一致性。

-   如果您認為實體必須進入無效狀態，請考慮使用不同的物件模型；例如，使用暫存 DTO，直到您建立最後一個領域實體。

-   如果您需要建立數個相關的物件 (例如彙總)，而且這些物件只有在全部建立之後才有效，請考慮使用 Factory 模式。

-   驗證架構是最適合用於特定層級，例如展示層或應用程式/服務層，但通常不適合用於領域模型層，因為您必須強烈依賴基礎結構架構。

-   在許多情況下，在用戶端重複驗證是不錯的做法，因為應用程式可以採取主動。


>[!div class="step-by-step"]
[上一個] (domain-model-layer-validations.md) [下一個] (domain-events-design-implementation.md)
