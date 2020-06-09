---
ms.openlocfilehash: b371525c9f4e57c6a09e5bb9232884e5c5e707e0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603003"
---

當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。 但是，如果您手動安裝 .NET Core 或發行獨立的應用程式，您必須確定已安裝這些程式庫：

- lttng-ust
- libcurl
- openssl-libs
- krb5-libs
- libicu
- zlib
- libunwind
- libuuid

如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您將需要安裝**相容性 compat-openssl10**。

如需相依性的詳細資訊，請參閱[獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。

針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：

- [libgdiplus （6.0.1 版或更新版本）](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > 您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的*libgdiplus* 。 如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。
