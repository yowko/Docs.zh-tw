---
ms.openlocfilehash: b371525c9f4e57c6a09e5bb9232884e5c5e707e0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603003"
---

<span data-ttu-id="36ec0-101">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="36ec0-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="36ec0-102">但是，如果您手動安裝 .NET Core 或發行獨立的應用程式，您必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="36ec0-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="36ec0-103">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="36ec0-103">lttng-ust</span></span>
- <span data-ttu-id="36ec0-104">libcurl</span><span class="sxs-lookup"><span data-stu-id="36ec0-104">libcurl</span></span>
- <span data-ttu-id="36ec0-105">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="36ec0-105">openssl-libs</span></span>
- <span data-ttu-id="36ec0-106">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="36ec0-106">krb5-libs</span></span>
- <span data-ttu-id="36ec0-107">libicu</span><span class="sxs-lookup"><span data-stu-id="36ec0-107">libicu</span></span>
- <span data-ttu-id="36ec0-108">zlib</span><span class="sxs-lookup"><span data-stu-id="36ec0-108">zlib</span></span>
- <span data-ttu-id="36ec0-109">libunwind</span><span class="sxs-lookup"><span data-stu-id="36ec0-109">libunwind</span></span>
- <span data-ttu-id="36ec0-110">libuuid</span><span class="sxs-lookup"><span data-stu-id="36ec0-110">libuuid</span></span>

<span data-ttu-id="36ec0-111">如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您將需要安裝**相容性 compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="36ec0-111">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="36ec0-112">如需相依性的詳細資訊，請參閱[獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="36ec0-112">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="36ec0-113">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="36ec0-113">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="36ec0-114">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="36ec0-114">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="36ec0-115">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的*libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="36ec0-115">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="36ec0-116">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="36ec0-116">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
