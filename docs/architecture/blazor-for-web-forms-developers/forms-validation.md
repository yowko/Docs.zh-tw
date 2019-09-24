---
title: 表單和驗證
description: 瞭解如何使用 Blazor 中的用戶端驗證來建立表單。
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: 9062e0ab106b7e647646bf5d206106153d7d9009
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214032"
---
# <a name="forms-and-validation"></a>表單和驗證

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web Forms 架構包含一組驗證服務器控制項，可處理輸入表單（`RequiredFieldValidator`、 `CompareValidator`、 `RangeValidator`等）的驗證使用者輸入。 ASP.NET Web Forms 架構也支援模型系結，並根據資料批註（`[Required]`、 `[StringLength]`、 `[Range]`等等）驗證模型。 您可以使用不顯眼的 JavaScript 驗證，在伺服器和用戶端上強制執行驗證邏輯。 `ValidationSummary`伺服器控制項是用來向使用者顯示驗證錯誤的摘要。

Blazor 支援在用戶端和伺服器之間共用驗證邏輯。 ASP.NET 提供許多一般伺服器驗證的預先建立 JavaScript。 在許多情況下，開發人員仍然必須撰寫 JavaScript，才能完全執行其應用程式特定的驗證邏輯。 相同的模型類型、資料批註和驗證邏輯可以同時在伺服器和用戶端上使用。

Blazor 提供一組輸入元件。 輸入元件會處理將欄位資料系結至模型，並在提交表單時驗證使用者輸入。

|輸入元件|呈現的 HTML 元素    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

元件會包裝這些輸入元件，並`EditContext`透過協調驗證程式。 `EditForm` 建立`EditForm`時，您可以`Model`使用參數來指定要系結的模型實例。 驗證通常是使用資料批註來完成，而且是可延伸的。 若要啟用以資料注釋為基礎的驗證`DataAnnotationsValidator` ，請將元件新增為`EditForm`的子系。 元件提供一個方便的事件來處理有效的`OnValidSubmit`（）和無效`OnInvalidSubmit`的（）提交。 `EditForm` 另外還有一個更通用`OnSubmit`的事件，可讓您自行觸發和處理驗證。

若要顯示驗證錯誤摘要，請使用`ValidationSummary`元件。 若要顯示特定輸入欄位的驗證訊息，請使用`ValidationMessage`元件，並針對指向適當模型成員`For`的參數指定 lambda 運算式。

下列模型類型使用資料批註來定義數個驗證規則：

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16, 
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000, 
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true", 
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

下列元件示範如何根據模型類型， `Starship`在 Blazor 中建立表單：

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

提交表單之後，就不會將模型系結資料儲存到任何資料存放區，例如資料庫。 在 Blazor WebAssembly 應用程式中，必須將資料傳送至伺服器。 例如，使用 HTTP POST 要求。 在 Blazor 伺服器應用程式中，資料已經在伺服器上，但必須保存。 在 Blazor apps 中處理資料存取是「[處理資料](data.md)」一節的主題。

## <a name="additional-resources"></a>其他資源

如需 Blazor apps 中[表單和驗證](/aspnet/core/blazor/forms-validation)的詳細資訊，請參閱 Blazor 檔。

>[!div class="step-by-step"]
>[上一頁](state-management.md)
>[下一頁](data.md)
