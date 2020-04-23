---
title: '.NET Framework 4.8、4.7、4.6 和 4.5 移轉手冊 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: fbaee646f7adcfe1a53d4231790e4258fd95a892
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102628"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a>移至 .NET 框架 4.8、4.7、4.6 和 4.5

如果使用早期版本的 .NET Framework 創建應用,通常可以將其升級到 .NET Framework 4.5 及其點版本(4.5.1 和 4.5.2)、.NET Framework 4.6 及其點版本(4.6.1 和 4.6.2)、.NET Framework 4.7 及其點版本(4.7.1 和 4.7.2)或 .NET Framework 4.8。 在 Visual Studio 中，開啟您的專案。 如果您的專案是使用舊版 Visual Studio 所建立，則會自動開啟 [專案相容性]**** 對話方塊。 如需升級 Visual Studio 專案的詳細資訊，請參閱[移植、移轉及升級 Visual Studio 專案](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)和 [Visual Studio 2019 平台目標及相容性](/visualstudio/releases/2019/compatibility)。

 但是,.NET 框架中的一些更改需要更改代碼。 您也可能想要利用 .NET Framework 4.5 及其小數點版本、.NET Framework 4.6 及其小數點版本、.NET Framework 4.7 及其小數點版本或 .NET Framework 4.8 中的某些新功能。 新增版本 .NET Framework 的應用程式進行這些類型的變更通常為*移轉*。 如果應用不必遷移,則可以在 .NET Framework 4.5 或更高版本中運行它,而無需重新編譯它。

## <a name="migration-resources"></a>移轉資源

將應用從早期版本的 .NET Framework 遷移到版本 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.6.2、4.7、4.7.1、4.7.2 或 4.8 之前,請查看以下文檔:

- 請參閱[版本和相依性](versions-and-dependencies.md)，了解每個 .NET Framework 版本的基礎 CLR 版本，並檢閱成功設定應用程式目標的方針。

- 查看[應用程式相容性](application-compatibility.md),瞭解可能影響應用的運行時更改和重新定位更改以及如何處理這些更改。

- 檢閱[類別庫中已淘汰的功能](../whats-new/whats-obsolete.md)，以判斷您的程式碼中可能已淘汰的任何類型或成員，以及建議的替代做法。

- 如需想要新增至應用程式之新功能的描述，請參閱[新功能](../whats-new/index.md)。

## <a name="see-also"></a>另請參閱

- [應用程式相容性](application-compatibility.md)
- [從 .NET Framework 1.1 移轉](migrating-from-the-net-framework-1-1.md)
- [版本相容性](version-compatibility.md)
- [版本和相依項](versions-and-dependencies.md)
- [如何:將應用設定為支援 .NET 框架 4 或更高版本](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [新功能](../whats-new/index.md)
- [類別庫中的過時功能](../whats-new/whats-obsolete.md)
- [.NET 框架官方支援政策](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [.NET Framework 4 移轉問題](net-framework-4-migration-issues.md)
