---
ms.openlocfilehash: 3d8179c5c0e84f8ff1197cce7790c80a5f5a4f6d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619441"
---

<span data-ttu-id="0e78c-101">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="0e78c-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="0e78c-102">但是，如果您手動安裝 .NET Core 或發行獨立的應用程式，您必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="0e78c-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="0e78c-103">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="0e78c-103">krb5-libs</span></span>
- <span data-ttu-id="0e78c-104">libicu</span><span class="sxs-lookup"><span data-stu-id="0e78c-104">libicu</span></span>
- <span data-ttu-id="0e78c-105">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="0e78c-105">openssl-libs</span></span>

<span data-ttu-id="0e78c-106">如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您將需要安裝**相容性 compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="0e78c-106">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="0e78c-107">如需相依性的詳細資訊，請參閱[獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="0e78c-107">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="0e78c-108">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="0e78c-108">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="0e78c-109">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="0e78c-109">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="0e78c-110">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的*libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="0e78c-110">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="0e78c-111">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="0e78c-111">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
