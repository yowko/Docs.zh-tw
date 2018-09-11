---
title: .NET Core 應用程式部署
description: 部署 .NET Core 應用程式。
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
ms.openlocfilehash: 2ef63ebd737739b2c8e671d982c3844135689ab4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277154"
---
# <a name="net-core-application-deployment"></a>.NET Core 應用程式部署

您可以建立兩種類型的 .NET Core 應用程式部署︰

- 與 Framework 相依的部署。 正如其名，與 Framework 相依的部署 (framework-dependent deployment, FDD) 仰賴存在於目標系統上的全系統共用 .NET Core 版本。 因為 .NET Core 已存在，所以應用程式也可以在 .NET Core 安裝之間攜帶。 您的應用程式僅包含其自有程式碼和 .NET Core 程式庫以外的所有協力廠商相依性。 FDD 包含的 *.dll* 檔案，可以使用 [dotnet 公用程式](../tools/dotnet.md)從命令列啟動。 例如，`dotnet app.dll` 執行名為 `app` 的應用程式。

- 自封式部署。 不同於 FDD，自封式部署 (SCD) 不仰賴任何存在於目標系統上的共用元件。 包括 .NET Core 程式庫和 .NET Core 執行階段的所有元件，都隨附於應用程式，並與其他 .NET Core 應用程式隔離。 SCD 包含可執行檔 (例如，Windows 平台上 `app` 應用程式的 *app.exe*)，這是重新命名的特定平台 .NET Core 主應用程式版本，以及實際的應用程式 *.dll* 檔案 (例如 *app.dll*)。

## <a name="framework-dependent-deployments-fdd"></a>與 Framework 相依的部署 (FDD)

針對 FDD，您只要部署您的應用程式與協力廠商相依性。 您不必部署 .NET Core，因為您的應用程式會使用存在於目標系統上的 .NET Core 版本。 這是以 .NET Core 為目標是 .NET Core 與 ASP.NET Core 應用程式的預設部署模型。

### <a name="why-create-a-framework-dependent-deployment"></a>為何建立與 Framework 相依的部署？

部署 FDD 有許多優點︰

- 您不必事先定義 .NET Core 應用程式執行所在的目標作業系統。 由於不論作業系統為何，.NET Core 對可執行檔和程式庫都使用通用的 PE 檔案格式，所以 .NET Core 可以執行您的應用程式，不理會基礎作業系統。 如需 PE 檔格式的詳細資訊，請參閱 [.NET Assembly File Format](../../standard/assembly-format.md) (.NET 組件檔案格式)。

- 部署套件的大小很小。 您只需要部署您的應用程式及其相依性，不用部署 .NET Core。

- 多個應用程式使用相同的 .NET Core 安裝，這樣可減少主機系統的磁碟空間和記憶體使用量。

另外還有幾個缺點︰

- 只有主機系統安裝了目標的 .NET Core 版本或更新版本，您的應用程式才能執行。

- .NET Core 執行階段和程式庫在未來的版本中可能有所變更，但不會通知您。 只有極其罕見的情況，才可能變更應用程式的行為。

## <a name="self-contained-deployments-scd"></a>自封式部署 (SCD)

針對自封式部署，您不僅要部署自己的應用程式和所有協力廠商相依性，還要部署建置應用程式所用的 .NET Core 版本。 不過，建立 SCD 不包含各種平台的 [.NET Core 原生相依性](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)本身 (例如，macOS 上的 OpenSSL)，所以在執行應用程式前要先行安裝。 如需執行階段之版本繫結的詳細資訊，請參閱 [.NET Core 中的版本繫結](../versions/selection.md)上的文章。

從 NET Core 2.1 SDK (2.1.300 版) 開始，.NET Core 就支援*修補版本向前復原*。 當您建立自封式部署時，.NET Core 工具會自動包括您的應用程式以其為目標的最新 .NET Core 維護執行階段版本 (最新的維護執行階段包括安全性修補程式與其他錯誤修正)。維護執行階段不需要存在於您的建置系統上，系統會自動從 NuGet.org 下載它。如需詳細資訊 (包括有關如何選擇退出修補版本向前復原的指示)，請參閱[自封式部署執行階段向前復原](runtime-patch-selection.md)。

FDD 和 SCD 使用不同的主機可執行檔，因此您可以使用自己的發行者簽章，為 SCD 簽署主機可執行檔。

### <a name="why-deploy-a-self-contained-deployment"></a>為什麼要部署自封式部署？

部署自封式部署有兩大優點︰

- 您可以獨家控制隨應用程式部署的 .NET Core 版本。 只有您可以提供 .NET Core 服務。

- 您可以保證目標系統能執行您的 .NET Core 應用程式，因為您提供的是它可以執行的 .NET Core 版本。

它也有一些缺點︰

- 因為 .NET Core 包含在您的部署套件中，所以您必須事先選取部署套件建置所在的目標平台。

- 您的部署套件的大小相當大，因為您必須包含 .NET Core 以及應用程式及其協力廠商相依性。

  從 .NET Core 2.0 開始，您就可以使用 .NET Core [*全球化不變模式*](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)來減少 Linux 系統上的部署大小大約 28 MB。 一般而言，Linux 上的 .NET Core 依賴 [ICU 程式庫](https://github.com/dotnet/docs/issues/http%22//icu-project.org)來提供全球化支援。 在不變模式中，程式庫不會包括在您的部署中，而且所有文化特性的行為都如[不變的文化特性](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)一樣。

- 將多個自封式 .NET Core 應用程式部署到系統，會消耗大量的磁碟空間，因為每個應用程式都會重複 .NET Core 檔案。

## <a name="step-by-step-examples"></a>逐步說明範例

如需使用 CLI 工具部署 .NET Core 應用程式的逐步說明範例，請參閱[使用 CLI 工具部署 .NET Core 應用程式](deploy-with-cli.md)。 如需使用 Visual Studio 部署 .NET Core 應用程式的逐步說明範例，請參閱[使用 Visual Studio 部署 .NET Core 應用程式](deploy-with-vs.md)。 每個主題都包含下列部署的範例：

- 與 Framework 相依的部署
- 有協力廠商相依性的 Framework 相依部署
- 自封式部署
- 有協力廠商相依性的自封式部署

## <a name="see-also"></a>另請參閱

* [使用 CLI 工具部署 .NET Core 應用程式](deploy-with-cli.md)
* [使用 Visual Studio 部署 .NET Core 應用程式](deploy-with-vs.md)
* [套件、中繼套件和架構](../packages.md)
* [.NET Core 執行階段識別項 (RID) 目錄](../rid-catalog.md)
