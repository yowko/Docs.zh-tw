---
title: 表單和驗證
description: 瞭解如何在中建立具有用戶端驗證功能的表單 Blazor 。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- Blazor WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: d2dce23996e996a736b04c9cdd1ccf3b549ff3ff
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267551"
---
# <a name="forms-and-validation"></a>表單和驗證

ASP.NET Web Forms framework 包含一組驗證服務器控制項，可處理驗證輸入表單中的使用者輸入， (、、等等 `RequiredFieldValidator` `CompareValidator` `RangeValidator`) 。 ASP.NET Web Forms framework 也支援模型系結，並根據資料批註來驗證模型 `[Required]` ， (、、 `[StringLength]` `[Range]` 等等) 。 您可以使用不顯眼的 JavaScript 驗證，在伺服器和用戶端上強制執行驗證邏輯。 `ValidationSummary`伺服器控制項是用來顯示驗證錯誤給使用者的摘要。

Blazor 支援在用戶端與伺服器之間共用驗證邏輯。 ASP.NET 提供許多常見伺服器驗證的預先建立 JavaScript 執行。 在許多情況下，開發人員仍必須撰寫 JavaScript，才能完全執行其應用程式專屬的驗證邏輯。 您可以在伺服器和用戶端上使用相同的模型類型、資料注釋和驗證邏輯。

Blazor 提供一組輸入元件。 輸入元件會處理系結欄位資料到模型，並在提交表單時驗證使用者輸入。

|輸入元件|轉譯的 HTML 元素    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

`EditForm`元件會包裝這些輸入元件，並透過來協調驗證流程 `EditContext` 。 建立時 `EditForm` ，您可以使用參數指定要系結的模型實例 `Model` 。 驗證通常是使用資料批註來完成，而且是可擴充的。 若要啟用以資料批註為基礎的驗證，請將 `DataAnnotationsValidator` 元件新增為的子系 `EditForm` 。 `EditForm`元件提供一個方便的事件來處理有效的 (`OnValidSubmit`) 和不正確 (`OnInvalidSubmit`) 提交。 另外還有一個更常見的 `OnSubmit` 事件，可讓您自行觸發和處理驗證。

若要顯示驗證錯誤摘要，請使用 `ValidationSummary` 元件。 若要顯示特定輸入欄位的驗證訊息，請使用 `ValidationMessage` 元件，為 `For` 指向適當模型成員的參數指定 lambda 運算式。

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

下列元件示範如何 Blazor 根據模型類型建立表單 `Starship` ：

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

提交表單之後，模型系結的資料尚未儲存到任何資料存放區，例如資料庫。 在 Blazor WebAssembly 應用程式中，必須將資料傳送到伺服器。 例如，使用 HTTP POST 要求。 在 Blazor 伺服器應用程式中，資料已在伺服器上，但必須保存。 處理應用程式中的資料存取 Blazor 是處理 [資料](data.md) 區段的主體。

## <a name="additional-resources"></a>其他資源

如需應用程式中 [表單和驗證](/aspnet/core/blazor/forms-validation) 的詳細資訊 Blazor ，請參閱 Blazor 檔。

>[!div class="step-by-step"]
>[上一個](state-management.md) 
>[下一步](data.md)
