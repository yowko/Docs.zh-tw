---
title: 開放原始碼 .NET 程式庫指導方針
description: 協助開發人員建立高品質 .NET 程式庫的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: 85d76c8b2bd0f030e3fbc1987e6ff51d6da44e76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644378"
---
# <a name="open-source-library-guidance"></a>開放原始碼程式庫指導

這份指導提供協助開發人員建立高品質 .NET 程式庫的最佳做法建議。 本文件的重點在於建置 .NET 程式庫時的「內容」與「原因」，而不是「方法」。

高品質開放原始碼 .NET 程式庫的各個層面：

> [!div class="checklist"]
> * **包山包海** - 致力於支援多種平台、程式設計語言與應用程式的優質 .NET 程式庫。
> * **穩定可靠** - 優質的 .NET 程式庫可在 .NET 生態環境中共存，能在使用多種程式庫建置而成的應用程式中執行。
> * **具備演進能力** - .NET 程式庫應該要隨著時間改善與演進，同時支援現有的使用者。
> * **可供偵錯** - .NET 程式庫應使用最新工具來為使用者打造良好的偵錯體驗。
> * **值得信賴** - .NET 程式庫使用安全性最佳做法來發行到 NuGet，以獲得開發人員的信任。

> [!div class="nextstepaction"]
> [開始使用](./get-started.md)

## <a name="types-of-recommendations"></a>建議類型

每篇文章都呈現四種類型的建議：**優先**、**考慮**、**避免**與**禁止**。 建議類型指出應遵循的程度。

您應該一律遵循**優先**類型的建議。 例如：

**✔️ 優先**使用 NuGet 套件散發您的程式庫。

至於**考慮**建議則通常應該遵循，但也會有不符合規則的例外，而您不必因為沒有遵循指導而感到自責：

**✔️ 考慮**使用 [SemVer 2.0.0](https://semver.org/) 來設定 NuGet 套件的版本。

**避免**建議指的是通常不建議採行的建議，但有時違反規則尚屬合理情況：

**❌ 避免**要求明確版本的 NuGet 套件參考。

最後，**禁止**類型的建議表示在多數情況下都不應採取的動作：

**❌ 禁止**發行程式庫的強式名稱和非強式名稱版本。 例如，`Contoso.Api` 和 `Contoso.Api.StrongNamed`。

>[!div class="step-by-step"]
>[下一步](get-started.md)
