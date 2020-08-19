---
title: .NET Framework 4.8、4.7、4.6 和 4.5 移轉手冊
description: 遷移至較新的 .NET Framework 版本的指南，其中包含新功能和應用程式相容性的資源。
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: c597f6e7b67e190ffe61a425506a1a34f254942c
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558500"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a>遷移至 .NET Framework 4.8、4.7、4.6 和4。5

如果您使用舊版 .NET Framework 建立應用程式，您通常可以將它升級為 .NET Framework 4.5 及其點發行版 (4.5.1 和 4.5.2) 、.NET Framework 4.6 及其點發行版 (4.6.1 和 4.6.2) 、.NET Framework 4.7 和其點發行版 (4.7.1 和 4.7.2) ，或輕鬆地 .NET Framework 4.8。 在 Visual Studio 中，開啟您的專案。 如果您的專案是使用舊版 Visual Studio 所建立，則會自動開啟 [專案相容性]**** 對話方塊。 如需升級 Visual Studio 專案的詳細資訊，請參閱[移植、移轉及升級 Visual Studio 專案](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)和 [Visual Studio 2019 平台目標及相容性](/visualstudio/releases/2019/compatibility)。

 不過，.NET Framework 中的某些變更需要變更您的程式碼。 您也可能想要利用 .NET Framework 4.5 及其小數點版本、.NET Framework 4.6 及其小數點版本、.NET Framework 4.7 及其小數點版本或 .NET Framework 4.8 中的某些新功能。 針對新版本的 .NET Framework，對您的應用程式進行這些類型的變更通常稱為「 *遷移*」。 如果您的應用程式不需要遷移，您可以在 .NET Framework 4.5 或更新版本中執行它，而不需要重新編譯。

## <a name="migration-resources"></a>移轉資源

將您的應用程式從舊版 .NET Framework 遷移至4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或4.8 版之前，請先參閱下列檔：

- 請參閱[版本和相依性](versions-and-dependencies.md)，了解每個 .NET Framework 版本的基礎 CLR 版本，並檢閱成功設定應用程式目標的方針。

- 請參閱 [應用程式相容性](application-compatibility.md) ，瞭解可能影響您應用程式的執行時間和重定目標變更，以及如何處理這些變更。

- 檢閱[類別庫中已淘汰的功能](../whats-new/whats-obsolete.md)，以判斷您的程式碼中可能已淘汰的任何類型或成員，以及建議的替代做法。

- 如需想要新增至應用程式之新功能的描述，請參閱[新功能](../whats-new/index.md)。

## <a name="see-also"></a>另請參閱

- [應用程式相容性](application-compatibility.md)
- [從 .NET Framework 1.1 移轉](migrating-from-the-net-framework-1-1.md)
- [版本相容性](version-compatibility.md)
- [版本和相依性](versions-and-dependencies.md)
- [如何：設定應用程式以支援 .NET Framework 4 或更新版本](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [新功能](../whats-new/index.md)
- [類別庫中的過時功能](../whats-new/whats-obsolete.md)
- [.NET Framework 官方支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [.NET Framework 4 移轉問題](net-framework-4-migration-issues.md)
