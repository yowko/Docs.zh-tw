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
# <a name="net-on-azure-development-environment-checklist"></a>Azure 開發環境上的 .NET 開發環境檢查清單

本檢查清單的目的是協助您確定已正確設定開發環境，以使用 Azure 進行 .NET 開發

## <a name="create-an-azure-account"></a>建立 Azure 帳戶

若要存取 Azure 服務或在 Azure 中執行應用程式，您需要 Azure 帳戶。

* 如果您是 Visual Studio 訂閱者，每月都有 [免費的 Azure 點數](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) 可供您使用
* [建立免費的 Azure 帳戶](https://azure.microsoft.com/free/dotnet/) 並獲得 $200 的點數，並免費選取免費的服務12個月
* 使用由貴公司的 Azure 系統管理員指派給您的帳戶

## <a name="configure-your-ide"></a>設定您的 IDE

Visual Studio 和 Visual Studio Code 等熱門工具都有擴充功能可讓您直接從 IDE 使用 Azure。

* 使用 Azure 設定適用于 .NET 開發的[Visual Studio](./configure-visual-studio.md)
* 使用 Azure 設定適用于 .NET 開發的[Visual Studio Code](./configure-vs-code.md)

## <a name="install-the-azure-cli"></a>安裝 Azure CLI

除了使用 Azure 入口網站之外，您還會想要安裝 Azure CLI 來建立和管理 Azure 資源。

* [安裝適用于 Windows) 的 Azure CLI](/cli/azure/install-azure-cli-windows?tabs=azure-cli)
* [安裝適用於 macOS 的 Azure CLI](/cli/azure/install-azure-cli-macos)
* [安裝適用于 Linux 的 Azure CLI](/cli/azure/install-azure-cli-linux)

## <a name="install-additional-tools-and-utilities"></a>安裝其他工具和公用程式

這些額外工具的設計可讓您在使用 Azure 時提高生產力。

* 如果您打算使用 PowerShell 腳本來建立和管理 Azure 資源，請[安裝 Azure PowerShell](/powershell/azure/install-az-ps)
* [安裝 Azure 儲存體總管](https://azure.microsoft.com/features/storage-explorer/) ，以上傳、下載及管理 Azure 儲存體資源中的資料，包括 blob、佇列、資料表和 CosmosDB。
* 如果您使用 Azure SQL，請[安裝 Azure Data Studio](/sql/azure-data-studio/download-azure-data-studio)

## <a name="bookmark-the-following-sites"></a>將下列網站加入書簽

在進行 Azure 開發時，您會經常使用這些網站。  將其加入書簽以供快速參考。

* Azure 入口網站- [https://portal.azure.com/](https://portal.azure.com/)
* Azure Cloud Shell- [https://shell.azure.com/](https://shell.azure.com/)
