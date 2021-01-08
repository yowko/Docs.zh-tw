---
title: Azure 設定檢查清單上的 .NET 開發
description: 提供您應該安裝的所有工具的快速摘要，以使用 Azure 進行 .net 開發
ms.date: 1/1/2021
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: a2ff9bbf1e6a8790ddc161a1a1c8d14e8fab6e41
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98027262"
---
# <a name="net-on-azure-development-environment-checklist"></a><span data-ttu-id="1cc4f-103">Azure 開發環境上的 .NET 開發環境檢查清單</span><span class="sxs-lookup"><span data-stu-id="1cc4f-103">.NET on Azure development environment checklist</span></span>

<span data-ttu-id="1cc4f-104">本檢查清單的目的是協助您確定已正確設定開發環境，以使用 Azure 進行 .NET 開發</span><span class="sxs-lookup"><span data-stu-id="1cc4f-104">This checklist is provided to help you make sure you have your development environment correctly configured for .NET development with Azure</span></span>

## <a name="create-an-azure-account"></a><span data-ttu-id="1cc4f-105">建立 Azure 帳戶</span><span class="sxs-lookup"><span data-stu-id="1cc4f-105">Create an Azure account</span></span>

<span data-ttu-id="1cc4f-106">若要存取 Azure 服務或在 Azure 中執行應用程式，您需要 Azure 帳戶。</span><span class="sxs-lookup"><span data-stu-id="1cc4f-106">To access Azure services or run applications in Azure, you need an Azure account.</span></span>

* <span data-ttu-id="1cc4f-107">如果您是 Visual Studio 訂閱者，每月都有 [免費的 Azure 點數](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) 可供您使用</span><span class="sxs-lookup"><span data-stu-id="1cc4f-107">If you are a Visual Studio subscriber, you have monthly [free Azure credits](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) available to you every month</span></span>
* <span data-ttu-id="1cc4f-108">[建立免費的 Azure 帳戶](https://azure.microsoft.com/free/dotnet/) 並獲得 $200 的點數，並免費選取免費的服務12個月</span><span class="sxs-lookup"><span data-stu-id="1cc4f-108">[Create a free Azure account](https://azure.microsoft.com/free/dotnet/) and receive $200 in credits and select services free for 12 months</span></span>
* <span data-ttu-id="1cc4f-109">使用由貴公司的 Azure 系統管理員指派給您的帳戶</span><span class="sxs-lookup"><span data-stu-id="1cc4f-109">Use an account assigned to you by your company's Azure administrator</span></span>

## <a name="configure-your-ide"></a><span data-ttu-id="1cc4f-110">設定您的 IDE</span><span class="sxs-lookup"><span data-stu-id="1cc4f-110">Configure your IDE</span></span>

<span data-ttu-id="1cc4f-111">Visual Studio 和 Visual Studio Code 等熱門工具都有擴充功能可讓您直接從 IDE 使用 Azure。</span><span class="sxs-lookup"><span data-stu-id="1cc4f-111">Popular tools like Visual Studio and Visual Studio Code have extensions available to let you work with Azure right from your IDE.</span></span>

* <span data-ttu-id="1cc4f-112">使用 Azure 設定適用于 .NET 開發的[Visual Studio](./configure-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="1cc4f-112">[Configure Visual Studio](./configure-visual-studio.md) for .NET development using Azure</span></span>
* <span data-ttu-id="1cc4f-113">使用 Azure 設定適用于 .NET 開發的[Visual Studio Code](./configure-vs-code.md)</span><span class="sxs-lookup"><span data-stu-id="1cc4f-113">[Configure Visual Studio Code](./configure-vs-code.md) for .NET Development using Azure</span></span>

## <a name="install-the-azure-cli"></a><span data-ttu-id="1cc4f-114">安裝 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="1cc4f-114">Install the Azure CLI</span></span>

<span data-ttu-id="1cc4f-115">除了使用 Azure 入口網站之外，您還會想要安裝 Azure CLI 來建立和管理 Azure 資源。</span><span class="sxs-lookup"><span data-stu-id="1cc4f-115">In addition to using the Azure portal, you will want to install the Azure CLI to create and manage Azure resources.</span></span>

* <span data-ttu-id="1cc4f-116">[安裝適用于 Windows) 的 Azure CLI](/cli/azure/install-azure-cli-windows?tabs=azure-cli)</span><span class="sxs-lookup"><span data-stu-id="1cc4f-116">[Install the Azure CLI for Windows](/cli/azure/install-azure-cli-windows?tabs=azure-cli))</span></span>
* [<span data-ttu-id="1cc4f-117">安裝適用於 macOS 的 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="1cc4f-117">Install the Azure CLI for macOS</span></span>](/cli/azure/install-azure-cli-macos)
* [<span data-ttu-id="1cc4f-118">安裝適用于 Linux 的 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="1cc4f-118">Install the Azure CLI for Linux</span></span>](/cli/azure/install-azure-cli-linux)

## <a name="install-additional-tools-and-utilities"></a><span data-ttu-id="1cc4f-119">安裝其他工具和公用程式</span><span class="sxs-lookup"><span data-stu-id="1cc4f-119">Install additional tools and utilities</span></span>

<span data-ttu-id="1cc4f-120">這些額外工具的設計可讓您在使用 Azure 時提高生產力。</span><span class="sxs-lookup"><span data-stu-id="1cc4f-120">These additional tools are designed to make you more productive when working with Azure.</span></span>

* <span data-ttu-id="1cc4f-121">如果您打算使用 PowerShell 腳本來建立和管理 Azure 資源，請[安裝 Azure PowerShell](/powershell/azure/install-az-ps)</span><span class="sxs-lookup"><span data-stu-id="1cc4f-121">[Install Azure PowerShell](/powershell/azure/install-az-ps) if you plan on using PowerShell scripts to create and manage Azure resources</span></span>
* <span data-ttu-id="1cc4f-122">[安裝 Azure 儲存體總管](https://azure.microsoft.com/features/storage-explorer/) ，以上傳、下載及管理 Azure 儲存體資源中的資料，包括 blob、佇列、資料表和 CosmosDB。</span><span class="sxs-lookup"><span data-stu-id="1cc4f-122">[Install Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) to upload, download, and manage data in Azure storage resources including blobs, queues, tables, and CosmosDB.</span></span>
* <span data-ttu-id="1cc4f-123">如果您使用 Azure SQL，請[安裝 Azure Data Studio](/sql/azure-data-studio/download-azure-data-studio)</span><span class="sxs-lookup"><span data-stu-id="1cc4f-123">[Install Azure Data Studio](/sql/azure-data-studio/download-azure-data-studio) if you are working with Azure SQL</span></span>

## <a name="bookmark-the-following-sites"></a><span data-ttu-id="1cc4f-124">將下列網站加入書簽</span><span class="sxs-lookup"><span data-stu-id="1cc4f-124">Bookmark the following sites</span></span>

<span data-ttu-id="1cc4f-125">在進行 Azure 開發時，您會經常使用這些網站。</span><span class="sxs-lookup"><span data-stu-id="1cc4f-125">You will use these sites frequently when doing Azure development.</span></span>  <span data-ttu-id="1cc4f-126">將其加入書簽以供快速參考。</span><span class="sxs-lookup"><span data-stu-id="1cc4f-126">Bookmark them for quick reference.</span></span>

* <span data-ttu-id="1cc4f-127">Azure 入口網站- [https://portal.azure.com/](https://portal.azure.com/)</span><span class="sxs-lookup"><span data-stu-id="1cc4f-127">Azure Portal - [https://portal.azure.com/](https://portal.azure.com/)</span></span>
* <span data-ttu-id="1cc4f-128">Azure Cloud Shell- [https://shell.azure.com/](https://shell.azure.com/)</span><span class="sxs-lookup"><span data-stu-id="1cc4f-128">Azure Cloud Shell - [https://shell.azure.com/](https://shell.azure.com/)</span></span>
