---
title: Azure SDK for .NET 總覽
description: 概要說明 Azure SDK for .NET 是什麼，以及在 .NET 應用程式中使用 SDK 的基本步驟
ms.date: 11/30/2020
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 3ec1ee9e8da3a6e03581ce2a29a655ec0d68fe54
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701070"
---
# <a name="azure-sdk-for-net-overview"></a><span data-ttu-id="b1c32-103">Azure SDK for .NET 總覽</span><span class="sxs-lookup"><span data-stu-id="b1c32-103">Azure SDK for .NET overview</span></span>

## <a name="what-is-the-azure-sdk-for-net"></a><span data-ttu-id="b1c32-104">什麼是 Azure SDK for .NET</span><span class="sxs-lookup"><span data-stu-id="b1c32-104">What is the Azure SDK for .NET</span></span>

<span data-ttu-id="b1c32-105">**AZURE SDK for .net** 的設計目的是要讓您輕鬆地從 .net 應用程式使用 azure 服務。</span><span class="sxs-lookup"><span data-stu-id="b1c32-105">The **Azure SDK for .NET** is designed to make it easy to use Azure services from your .NET applications.</span></span>  <span data-ttu-id="b1c32-106">無論是將檔案上傳和下載到 Blob 儲存體、從 Azure Key Vault 取出應用程式秘密，還是從 Azure 事件中樞處理通知，Azure SDK for .NET 都提供一致且熟悉的介面來存取 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="b1c32-106">Whether it is uploading and downloading files to Blob Storage, retrieving application secrets from Azure Key Vault, or processing notifications from Azure Event Hubs, the Azure SDK for .NET provides a consistent and familiar interface to access Azure services.</span></span>  

<span data-ttu-id="b1c32-107">Azure SDK for .NET 是以 NuGet 套件系列的形式提供，可在 .NET Core (2.1 和更新版本) 和 .NET Framework (4.6.1 和更高的) 應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="b1c32-107">The Azure SDK for .NET is available as series of NuGet packages that can be used in both .NET Core (2.1 and higher) and .NET Framework (4.6.1 and higher) applications.</span></span>

![顯示 .NET 應用程式如何使用 Azure SDK 來存取 Azure 服務的圖表](./media/azure-sdk-for-dotnet-overview.png)

## <a name="use-the-azure-sdk-for-net-in-your-applications"></a><span data-ttu-id="b1c32-109">在您的應用程式中使用 Azure SDK for .NET</span><span class="sxs-lookup"><span data-stu-id="b1c32-109">Use the Azure SDK for .NET in your applications</span></span>

<span data-ttu-id="b1c32-110">若要在您的其中一個 .NET 應用程式中使用 Azure SDK 封裝，您需要遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="b1c32-110">To use an Azure SDK package in one of your .NET applications, you want to follow these steps.</span></span>

1. <span data-ttu-id="b1c32-111">**找出適當的 SDK 套件-** 使用 [套件清單](../packages.md) 來尋找適用于您所使用之 Azure 服務的適當套件。</span><span class="sxs-lookup"><span data-stu-id="b1c32-111">**Locate the appropriate SDK package -** Use the [package list](../packages.md) to find the appropriate package for the Azure service you are working with.</span></span>  <span data-ttu-id="b1c32-112">請注意，大部分的服務都有用戶端封裝可使用服務，以及用來建立和管理服務實例的管理套件。</span><span class="sxs-lookup"><span data-stu-id="b1c32-112">Be advised that most services have a client package for working with the service and a management package for creating and managing instances of the service.</span></span>  <span data-ttu-id="b1c32-113">在大部分情況下，您會想要用戶端套件。</span><span class="sxs-lookup"><span data-stu-id="b1c32-113">In most cases, you will want the client package.</span></span>  <span data-ttu-id="b1c32-114">使用 NuGet 在您的應用程式中安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="b1c32-114">Install this package in your application using NuGet.</span></span>

2. <span data-ttu-id="b1c32-115">**設定應用程式的驗證-** 若要存取 Azure 資源，您的應用程式將需要在 Azure 中指派適當的認證和存取權限。</span><span class="sxs-lookup"><span data-stu-id="b1c32-115">**Set up authentication for your application -** To access Azure resources, your application will need to have the appropriate credentials and access rights assigned in Azure.</span></span>  <span data-ttu-id="b1c32-116">瞭解如何設定驗證以驗證 [.net 應用程式至 Azure](../authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="b1c32-116">Learn how to configure authentication in [Authenticating .NET applications to Azure](../authentication.md).</span></span>

3. <span data-ttu-id="b1c32-117">**在您的應用程式中使用 SDK 撰寫程式碼-** 使用 Azure 服務時，您的程式碼會先建立用戶端物件來使用服務，然後在該用戶端物件上呼叫方法，以與服務進行互動。</span><span class="sxs-lookup"><span data-stu-id="b1c32-117">**Write code using the SDK in your application -** When working with Azure services, your code will first create a client object to work with the service and then call methods on that client object to interact with the service.</span></span>  <span data-ttu-id="b1c32-118">同時提供同步和非同步方法。</span><span class="sxs-lookup"><span data-stu-id="b1c32-118">Both synchronous and asynchronous methods are provided.</span></span>  <span data-ttu-id="b1c32-119">Azure 檔中提供了使用每個個別 SDK 套件的範例。</span><span class="sxs-lookup"><span data-stu-id="b1c32-119">Examples of using each individual SDK package are provided throughout the Azure documentation.</span></span>

4. <span data-ttu-id="b1c32-120">**設定 SDK 的記錄 (選擇性) -** 如果您需要診斷您的應用程式與 Azure 之間的問題，您可以 [在 AZURE SDK for .net 中啟用記錄功能](./logging.md)。</span><span class="sxs-lookup"><span data-stu-id="b1c32-120">**Configure logging for the SDK (optional) -** If you need to diagnose issues between your application and Azure, you can [enable logging in the Azure SDK for .NET](./logging.md).</span></span>
