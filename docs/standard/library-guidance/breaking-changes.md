---
title: 中斷性變更與 .NET 程式庫
description: 建立 .NET 程式庫時巡覽中斷性變更的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: a5cfd2dfb544b2e47a87bd0939990ae73e5eda9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564220"
---
# <a name="breaking-changes"></a>重大變更

.NET 程式庫必須在針對現有使用者提供穩定性，以及針對未來取得創新之間取得平衡。 程式庫作者會傾向重構及重新思考程式碼，直到他們的程式庫完美為止，但中斷您現有的使用者可能會帶來負面影響 (尤其是低層級的程式庫)。

## <a name="project-types-and-breaking-changes"></a>專案類型與中斷性變更

.NET 社群使用程式庫的方式會改變中斷性變更對終端使用者開發人員的影響。

* **低層級與中層級程式庫** (例如序列化程式、HTML 剖析器、資料庫物件關聯式對應程式或 Web 架構) 受到中斷性變更的影響程度最大。

  終端使用者開發人員會使用建置組塊套件來建置應用程式，其他程式庫則會將建置組塊套件用來作為 NuGet 相依性。 例如，您要建置一個應用程式，且使用開放原始碼用戶端來呼叫 Web 服務。 對使用者所使用相依性進行的中斷性變更，便不是您可以修正的項目。 因為需要變更的是開放原始碼用戶端，而您無法控制該用戶端。 您必須找出程式庫的相容版本，或是提交用戶端程式庫的修正並等待新版本。 最差的情況便是您想要使用兩個相依於不同版本協力廠商程式庫的程式庫，而這兩個版本彼此互不相容。

* **高層級程式庫**(例如 UI 控制項套件) 受到中斷性變更影響的程度則較低。

  終端使用者應用程式中會直接參考高層級程式庫。 若發生中斷性變更，開發人員可以選擇更新到最新版本，或是修改他們的應用程式來配合中斷性變更。

**✔️ 請**思考您程式庫的使用方式。 中斷性變更可能會對使用它的應用程式和程式庫帶來什麼影響？

**✔️ 請**在開發低層級 .NET 程式庫時，盡量避免中斷性變更。

**✔️ 請考慮**將大幅重寫的程式庫作為新的 NuGet 套件發佈。

## <a name="types-of-breaking-changes"></a>中斷性變更的類型

中斷性變更可分成不同類別，其影響的程度各不相同。

### <a name="source-breaking-change"></a>原始檔中斷性變更

原始檔中斷性變更不會影響程式的執行，但是會在下一次重新編譯應用程式時導致編譯錯誤。 例如，新的多載可能會在先前明確的方法呼叫過程中造成模稜兩可的情況；重新命名參數則可能會中斷使用具名參數的呼叫者。

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

因為原始檔中斷性變更只會在開發人員重新編譯應用程式時造成傷害，因此它是干擾程度最小的中斷性變更。 開發人員可以輕易地自行修正中斷的原始程式碼。

### <a name="behavior-breaking-change"></a>行為中斷性變更

行為中斷性變更是最常見的中斷性變更類型：對行為進行的任何變更幾乎都會中斷其他人。 變更您的程式庫 (例如方法簽章、擲回的例外狀況或是輸入或輸出資料格式) 都可能會對您程式庫的消費者帶來負面影響。 若使用者依賴先前中斷的行為，即使是修正 Bug 都可能會符合中斷性變更的定義。

新增功能和改善不良行為是件好事，但若不小心，便可能會讓現有使用者難以進行升級。 協助開發人員處理行為中斷性變更的其中一種方法，便是將它們隱藏在設定後方。 設定可以讓開發人員更新到程式庫的最新版本，同時也能讓他們選擇加入或退出中斷性變更。 這項策略可讓開發人員維持在最新狀態，同時也能讓他們取用的程式碼隨時間適應變更。

例如，ASP.NET Core MVC 具有[相容性版本](/aspnet/core/mvc/compatibility-version)的概念，可修改在 `MvcOptions` 上啟用或停用的功能。

**✔️ 請考慮**在新功能可能影響現有使用者的情況下，根據預設將其維持在關閉狀態，並讓開發人員透過設定加入功能。

### <a name="binary-breaking-change"></a>二進位中斷性變更

二進位中斷性變更會在您變更程式庫的公用 API 時發生，導致針對您舊版程式庫進行編譯的組件無法繼續呼叫 API。 例如，新增新參數來變更方法的簽章會導致針對舊版程式庫進行編譯的組件擲回 <xref:System.MissingMethodException>。

二進位中斷性變更也可能會中斷**整個組件**。 使用 `AssemblyName` 重新命名組件，或是新增、移除或變更組件的強式命名金鑰，則會變更組件的身分識別。 變更組件的身分識別會中斷所有使用它的編譯程式碼。

**❌ 請不要**變更組件名稱。

**❌ 請不要**新增、移除或變更強式命名金鑰。

**✔️ 請考慮**使用抽象基底類別，而非介面。

> 將任何項目新增到介面都會造成實作它的現有類型失敗。 基底類別則允許您新增預設虛擬實作。

**✔️ 請考慮**將 <xref:System.ObsoleteAttribute> 放置在您打算移除的類型和成員上。 屬性應具備指示，說明如何更新程式碼以避免使用已淘汰的 API。

> 呼叫具有 <xref:System.ObsoleteAttribute> 類型和方法的程式碼會產生建置警告，並附帶提供給該屬性的訊息。 警告可讓使用已淘汰 API 的人員進行遷移，以在移除已淘汰的 API 時，大多數的人員已不再使用它。

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

**✔️ 請考慮**在低層級與中層級程式庫中無限期維持具有 <xref:System.ObsoleteAttribute> 的類型和方法。

> 移除 API 是一項二進位中斷性變更。 若維持已淘汰類型和方法的成本低廉，也不會為您的程式庫增加技術債務，則請考慮維持已淘汰的類型和方法。 避免移除類型和方法，可協助避免上述提到的最差情況。

## <a name="see-also"></a>另請參閱

- [適用於 C# 開發人員的版本和更新考量](../../csharp/whats-new/version-update-considerations.md)
- [A definitive guide to API-breaking changes in .NET](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net) (.NET 中 API 中斷性變更的完整指南)
- [CoreFX Breaking Change Rules](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md) (CoreFX 中斷性變更規則)

>[!div class="step-by-step"]
>[上一步](versioning.md)
