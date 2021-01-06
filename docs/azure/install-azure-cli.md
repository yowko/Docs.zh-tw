---
title: 安裝 Azure CLI
description: Azure 開發人員將需要安裝 Azure CLI，因此本文說明為何您需要 CLI，以及從何處下載並安裝它。
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 43737aaf5dfd02b8c4ffa6c213d7221cfe38162f
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701099"
---
# <a name="install-the-azure-cli"></a><span data-ttu-id="b2d71-103">安裝 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="b2d71-103">Install the Azure CLI</span></span>

<span data-ttu-id="b2d71-104">除了 Azure 入口網站，Azure 也會提供 [Azure CLI](/cli/azure/) 作為命令列工具，以建立和管理 azure 資源。</span><span class="sxs-lookup"><span data-stu-id="b2d71-104">In addition to the Azure Portal, Azure also offers the [Azure CLI](/cli/azure/) as a command-line tool to create and manage Azure resources.</span></span> <span data-ttu-id="b2d71-105">Azure CLI 提供效率、重複性和編寫週期性工作腳本的能力。</span><span class="sxs-lookup"><span data-stu-id="b2d71-105">The Azure CLI offers the benefits of efficiency, repeatability, and the ability to script recurring tasks.</span></span>  

<span data-ttu-id="b2d71-106">在實務上，大部分的開發人員會使用 Azure 入口網站和 Azure CLI。</span><span class="sxs-lookup"><span data-stu-id="b2d71-106">In practice, most developers use both the Azure Portal and the Azure CLI.</span></span> <span data-ttu-id="b2d71-107">在 Azure 入口網站中，當您探索新的服務，並瞭解 Azure 帳戶中的所有資源時，大部分的開發人員會發現 Azure CLI 更快且更有效率。</span><span class="sxs-lookup"><span data-stu-id="b2d71-107">Where as the Azure Portal is useful when exploring new services and getting an overview of all of the resources in your Azure account, most developers find the Azure CLI to be faster and more efficient.</span></span>  <span data-ttu-id="b2d71-108">Azure CLI 通常可以在單一命令中完成，而在 Azure 入口網站中會執行多個步驟。</span><span class="sxs-lookup"><span data-stu-id="b2d71-108">The Azure CLI can often accomplish in a single command what takes multiple steps in the Azure Portal.</span></span>  <span data-ttu-id="b2d71-109">此外，由於 Azure CLI 命令可儲存至檔案，因此開發人員可以確保每次都會以相同的方式執行循環性的工作。</span><span class="sxs-lookup"><span data-stu-id="b2d71-109">In addition, since Azure CLI commands can be saved to a file, developers can assure that recurrent tasks are run the same way each time.</span></span>

<span data-ttu-id="b2d71-110">Azure CLI 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="b2d71-110">The Azure CLI is available for Windows, macOS, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2d71-111">安裝適用於 Windows 的 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="b2d71-111">Install the Azure CLI for Windows</span></span>](/cli/azure/install-azure-cli-windows?tabs=azure-cli)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2d71-112">安裝適用於 macOS 的 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="b2d71-112">Install the Azure CLI for macOS</span></span>](/cli/azure/install-azure-cli-macos)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2d71-113">安裝適用于 Linux 的 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="b2d71-113">Install the Azure CLI for Linux</span></span>](/cli/azure/install-azure-cli-linux)

### <a name="azure-cloud-shell"></a><span data-ttu-id="b2d71-114">Azure Cloud Shell</span><span class="sxs-lookup"><span data-stu-id="b2d71-114">Azure Cloud Shell</span></span>

<span data-ttu-id="b2d71-115">您也可以使用 Azure Cloud Shell 中的 Azure CLI [https://shell.azure.com](https://shell.azure.com) 。</span><span class="sxs-lookup"><span data-stu-id="b2d71-115">You can also use the Azure CLI in the Azure Cloud Shell at [https://shell.azure.com](https://shell.azure.com).</span></span>  <span data-ttu-id="b2d71-116">Azure Cloud Shell 是可用於管理 Azure 資源的功能完整、以瀏覽器為基礎的 Shell。</span><span class="sxs-lookup"><span data-stu-id="b2d71-116">The Azure Cloud Shell is a fully functional, browser-based shell for managing Azure resources.</span></span>  <span data-ttu-id="b2d71-117">當您需要命令列環境，但在無法安裝 Azure CLI 的裝置上工作時，Azure Cloud Shell 會很有用。</span><span class="sxs-lookup"><span data-stu-id="b2d71-117">The Azure Cloud Shell is useful when you need a command line environment but are working on a device where you are unable to install the Azure CLI.</span></span>

![在瀏覽器中執行之 Azure Cloud Shell 的螢幕擷取畫面](media/azure-cloud-shell.png)
