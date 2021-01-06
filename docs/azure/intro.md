---
title: 開始使用 Azure 與 .NET
description: 了解您需要知道的 Azure 和 .NET 基本概念。
ms.date: 06/20/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 5d14bd0d9930d41a8c60b58b9f5b0522f0c0e398
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700767"
---
# <a name="introduction-to-azure-and-net"></a>Azure 與 .NET 簡介

## <a name="what-is-azure"></a>何謂 Azure？

Azure 是一個雲端平臺，旨在簡化新式應用程式的建立流程。  無論您選擇將應用程式完全裝載在 Azure 中，或使用 Azure 服務擴充您的內部部署應用程式，Azure 都可協助您建立可調整、可靠且可維護的應用程式。  隨著您已經使用的工具廣泛支援，例如 Visual Studio 和 Visual Studio Code 以及全方位的 SDK 程式庫，Azure 的設計可讓您從一開始就能成為 .NET 開發人員的生產力。

## <a name="application-development-scenarios-on-azure"></a>Azure 上的應用程式開發案例

您可以根據您的需求，以不同的方式將 Azure 納入您的應用程式。

- **裝載在 Azure 上的應用程式-** Azure 可以將整個應用程式堆疊從 web 應用程式和 Api 裝載到儲存體服務的資料庫。 Azure 支援各種不同的裝載模型，從完全受控的服務到容器到虛擬機器。 使用完全受控的 Azure 服務時，您的應用程式可以利用 Azure 中內建的擴充性、高可用性和安全性。

- **從應用程式使用雲端服務-** 現有的應用程式可以併入 Azure 服務，以擴充其功能。  這可能包括使用 [Azure 認知搜尋](/azure/search/search-what-is-azure-search)新增全文檢索搜尋功能、將應用程式秘密安全地儲存在 [Azure Key Vault](/azure/key-vault/) ，或使用 [Azure 認知服務](/azure/cognitive-services/)來新增視覺、語音和語言理解功能。  這些服務完全由 Azure 管理，而且可以輕鬆地新增至您的應用程式，而不需要變更您目前的應用程式架構或部署模型。

- **新式無伺服器架構-** Azure Functions 簡化建立解決方案來處理事件驅動的工作流程、回應 HTTP 要求、處理 Blob 儲存體中的檔案上傳，或處理佇列中的事件。  您只需撰寫處理事件所需的程式碼，而不需要擔心伺服器或架構程式碼。  此外，您可以利用超過250個連接器來處理其他 Azure 和協力廠商服務，以解決最棘手的整合問題。

## <a name="access-azure-services-from-net-applications"></a>從 .NET 應用程式存取 Azure 服務

無論您的應用程式是裝載于 Azure 或內部部署，大部分 Azure 服務的存取都是透過 **AZURE SDK for .net** 提供。  Azure SDK for .NET 是以一系列 NuGet 套件的形式提供，可在 .NET Core (2.1 和更新版本) 和 .NET Framework (4.6.1 和更高的) 應用程式中使用。 Azure SDK for .NET 可讓您輕鬆地將 Azure 服務整合到您的應用程式中，只要安裝正確的 NuGet 套件、將用戶端物件具現化，然後呼叫適當的方法即可。 如需 Azure SDK for .NET 的詳細資訊，請參閱 [AZURE sdk for .Net 總覽](./sdk/azure-sdk-for-dotnet.md)。

![顯示 .NET 應用程式如何使用 Azure SDK 來存取 Azure 服務的圖表](./media/azure-sdk-for-dotnet-overview.png)

## <a name="next-steps"></a>後續步驟

接下來，瞭解最 [常使用的 Azure 服務](./key-azure-services.md) 以進行 .net 開發。
