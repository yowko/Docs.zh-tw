---
title: 重大變更 」 和 「.NET 程式庫
description: 瀏覽時建立的.NET 程式庫的重大變更的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 83c01fdad7d836877bf692b87eeb0230219ded36
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49369807"
---
# <a name="breaking-changes"></a>重大變更

很重要的.NET 程式庫，若要尋找現有使用者的穩定性和未來的創新之間取得平衡。 程式庫作者借助針對重構和重新思考程式碼，直到它是完美的但是中斷現有的使用者會有負面的影響，特別是針對低層級的程式庫。

## <a name="project-types-and-breaking-changes"></a>專案類型和重大變更

.NET 社群使用文件庫的方式變更使用者的開發人員的重大變更的影響。

* **低和中介層程式庫**等序列化程式、 HTML 剖析器、 資料庫物件關聯式對應程式或 web 架構是最受影響的重大變更。

  建置組塊套件會使用由使用者來建置應用程式的開發人員和其他程式庫做為 NuGet 相依性。 例如，您要建置的應用程式，並使用開放原始碼用戶端來呼叫 web 服務。 用戶端會使用相依性的重大更新不是您可以修正。 它是開放原始碼用戶端，需要變更，就無法控制。 您必須尋找相容版本的程式庫或提交修正，以用戶端程式庫，並等候新的版本。 最糟的情況是如果您想要使用相依於彼此不相容的版本，第三個程式庫的兩個程式庫。

* **高層級的程式庫**像一套的 UI 控制項是較不容易的重大變更。

  高層級的程式庫會直接參考使用者應用程式中。 如果發生重大變更，開發人員可以選擇更新為最新版本，或可以修改其應用程式使用的重大變更。

**請勿 ✔️**思考您的程式庫的使用方式。 重大變更會有何種影響的應用程式和程式庫，使用它呢？

**請勿 ✔️**開發的低層級的.NET 程式庫時，將重大變更降至最低。

**請考慮 ✔️**發行主要重寫為新的 NuGet 套件程式庫。

## <a name="types-of-breaking-changes"></a>類型的重大變更

重大變更會分成不同類別，並不是同樣有影響力。

### <a name="source-breaking-change"></a>來源重大變更

重大變更的來源並不會影響程式執行，但會導致重新編譯應用程式在下一次編譯錯誤。 比方說，新的多載可以在先前模稜兩可，方法呼叫的模稜兩可，或已重新命名的參數將會中斷的呼叫端使用具名參數。

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

開發人員重新編譯其應用程式時，才會造成損害的重大變更的來源，因為它會是最少干擾的重大變更。 開發人員可以輕鬆地修正自己中斷的來源的程式碼。

### <a name="behavior-breaking-change"></a>行為重大變更

行為變更是最常見的重大變更的類型： 幾乎任何行為變更可能會中斷其他人。 變更為您的程式庫，例如方法簽章，例外狀況擲回或輸入或輸出資料格式，所有設定而嚴重影響您的程式庫取用者。 如果使用者依賴先前中斷的行為，甚至修正可以限定為一項重大變更。

新增功能和改善不正確的行為是件好事，但是不小心會變得更難升級現有的使用者。 若要協助開發人員在面對重大變更的行為的其中一個方法是設定背後隱藏起來。 設定可讓開發人員更新您的程式庫，而同時選擇參加或退出的重大變更最新版本。 這項策略可讓開發人員同時可讓其使用的程式碼，採用經過一段時間保持最新狀態。

例如，ASP.NET Core MVC 具有概念[相容性版本](/aspnet/core/mvc/compatibility-version)修改的功能已啟用和停用`MvcOptions`。

**請考慮 ✔️**離開的新功能，根據預設，如果它們會影響現有的使用者，讓開發人員選擇加入設定的功能。

### <a name="binary-breaking-change"></a>二進位的重大變更

當您變更您的程式庫的公用 API 時，會發生重大變更的二進位檔，因此對編譯的組件較舊版本的程式庫已不再能夠呼叫 API。 例如，藉由新增新的參數變更方法簽章會對程式庫的較舊版本所編譯的組件會擲回<xref:System.MissingMethodException>。

重大變更的二進位檔可能會破壞**整個組件**。 重新命名的組件`AssemblyName`，將組件的身分識別，也會新增、 移除或變更組件的強式命名金鑰。 組件的身分識別的變更會中斷所有使用它的已編譯程式碼。

**不這麼做 ❌**變更組件名稱。

**不這麼做 ❌**新增、 移除或變更的強式命名的索引鍵。

**請考慮 ✔️**使用抽象的基底類別，而不介面。

> 將任何項目新增至介面，會導致現有的型別實作失敗。 抽象基底類別可讓您新增的預設虛擬實作。

**請考慮 ✔️**放置<xref:System.ObsoleteAttribute>類型和您想要移除的成員。 屬性應該更新程式碼的指示進行，不能再使用過時的 API。

> 呼叫類型和方法的程式碼<xref:System.ObsoleteAttribute>會產生建置警告並提供給屬性的訊息。 警告讓人使用過時的 API 介面的時間來移轉，如此當移除過時的 API 時，大部分都不會再使用它。

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

## <a name="see-also"></a>另請參閱

* [適用於 C# 開發人員版和更新的考量](../../csharp/whats-new/version-update-considerations.md)
* [在.NET 中的 API-重大變更指南](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
* [CoreFX 重大變更規則](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
[上一步](./versioning.md)
