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
# <a name="azure-sdk-for-net-overview"></a>Azure SDK for .NET 總覽

## <a name="what-is-the-azure-sdk-for-net"></a>什麼是 Azure SDK for .NET

**AZURE SDK for .net** 的設計目的是要讓您輕鬆地從 .net 應用程式使用 azure 服務。  無論是將檔案上傳和下載到 Blob 儲存體、從 Azure Key Vault 取出應用程式秘密，還是從 Azure 事件中樞處理通知，Azure SDK for .NET 都提供一致且熟悉的介面來存取 Azure 服務。  

Azure SDK for .NET 是以 NuGet 套件系列的形式提供，可在 .NET Core (2.1 和更新版本) 和 .NET Framework (4.6.1 和更高的) 應用程式中使用。

![顯示 .NET 應用程式如何使用 Azure SDK 來存取 Azure 服務的圖表](./media/azure-sdk-for-dotnet-overview.png)

## <a name="use-the-azure-sdk-for-net-in-your-applications"></a>在您的應用程式中使用 Azure SDK for .NET

若要在您的其中一個 .NET 應用程式中使用 Azure SDK 封裝，您需要遵循下列步驟。

1. **找出適當的 SDK 套件-** 使用 [套件清單](../packages.md) 來尋找適用于您所使用之 Azure 服務的適當套件。  請注意，大部分的服務都有用戶端封裝可使用服務，以及用來建立和管理服務實例的管理套件。  在大部分情況下，您會想要用戶端套件。  使用 NuGet 在您的應用程式中安裝此套件。

2. **設定應用程式的驗證-** 若要存取 Azure 資源，您的應用程式將需要在 Azure 中指派適當的認證和存取權限。  瞭解如何設定驗證以驗證 [.net 應用程式至 Azure](../authentication.md)。

3. **在您的應用程式中使用 SDK 撰寫程式碼-** 使用 Azure 服務時，您的程式碼會先建立用戶端物件來使用服務，然後在該用戶端物件上呼叫方法，以與服務進行互動。  同時提供同步和非同步方法。  Azure 檔中提供了使用每個個別 SDK 套件的範例。

4. **設定 SDK 的記錄 (選擇性) -** 如果您需要診斷您的應用程式與 Azure 之間的問題，您可以 [在 AZURE SDK for .net 中啟用記錄功能](./logging.md)。
