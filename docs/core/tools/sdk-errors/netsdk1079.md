---
title: NETSDK1079：以 .NET Core 3.0 或更高版本為目標時，不支援 AspNetCore. 所有套件。
description: 如何解決 AspNetCore 應用程式的遷移
author: dsplaisted
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1079
ms.openlocfilehash: e0b7aba909dbd2931f755238a2de2418d294751d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445749"
---
# <a name="netsdk1079-the-microsoftaspnetcoreall-package-is-not-supported-when-targeting-net-core-30-or-higher"></a>NETSDK1079：以 .NET Core 3.0 或更高版本為目標時，不支援 AspNetCore. 所有套件。

本文 **適用于：** ✔️ .NET Core SDK 3.1.100 和更新版本

當下列情況時，您可能會收到此錯誤訊息：

- 您將 ASP.NET Core 專案從 .NET Core 2.2 或更舊版本重定為 .NET Core 3.0 或更新版本。
- 專案會使用 AspNetCore. All 套件。

移除 AspNetCore 的。 `PackageReference`  您也可能需要為 AspNetCore 所參考的封裝新增套件參考，但不包含在 ASP.NET Core 的共用架構中。  這些套件列在這裡：[從 AspNetCore 遷移至 AspNetCore。](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp)

另請參閱 [從 ASP.NET Core 2.2 遷移至 3.0](/aspnet/core/migration/22-to-30)
