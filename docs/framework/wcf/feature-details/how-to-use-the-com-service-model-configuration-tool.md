---
title: 作法：使用 COM+ 服務模型組態工具
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 2d21ec8ccf84a7c9af235af8e0afd444044cf81b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729383"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>作法：使用 COM+ 服務模型組態工具

一旦您選取了適當的裝載模式，請使用 COM+ 服務模型組態命令列工具 (ComSvcConfig.exe) 來設定將公開為 Web 服務的應用程式介面。

> [!NOTE]
> 您必須是電腦的系統管理員，才能執行下列任何一項工作。

 在 Windows 7 電腦上使用 ComSvcConfig.exe 設定 Web 服務以使用最新的服務模型版本 (目前為 4.5 版) 時，請執行下列步驟：

1. 將登錄機碼設定  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` 為 DWORD 值0x00000001

2. 執行 comsvcconfig.exe

3. 將步驟 1 新增的登錄機碼還原成其原始值，或將它刪除 (如果不存在的話)。

> [!IMPORTANT]
> 將這個登錄機碼還原是非常重要的步驟。 此為相容性的關鍵。 未還原這項變更可能會導致在電腦上執行的其他 .NET 應用程式發生問題)。

> [!WARNING]
> 在 Windows 8 電腦上使用 ComSvcConfig.exe/install 時，會顯示一個對話方塊，指出「您電腦上的應用程式需要下列 Windows 功能： .NET Framework 3.5 (包括 .NET 2.0 和 .NET 3.0」（如果未安裝 .NET Framework 3.5）。 您可以忽略這個對話方塊， 也可以將 OnlyUseLatestCLR 登錄機碼設定為 DWORD 值 (0x00000001)

## <a name="add-an-interface-using-the-com-hosting-mode"></a>使用 COM + 裝載模式加入介面

- 請使用 `/install` 和 `/hosting:complus` 選項來執行 ComSvcConfig，如下列範例所示。

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose
    ```

     此命令會將 `IFinances` 元件的 `ItemOrders.IFinancial` 介面 (來自 OnlineStore COM+ 應用程式) 新增到即將公開為 Web 服務的介面集合。 服務將使用 COM+ 裝載模式，因此需要明確的應用程式啟動。

     雖然萬用字元星號 (\*) 字元可以用於元件和介面，但請避免使用它，因為您可能只想要將選取的功能公開為 Web 服務。 如果與此元件的未來版本一起執行，使用萬用字元會不小心將決定組態語法時尚不存在的介面一併公開出來。

     /verbose 選項會指示工具在任何錯誤旁邊加上警告。

     公開服務的合約將包含來自 `IFinances` 介面的所有方法。

## <a name="add-specific-methods-from-an-interface-using-the-com-hosting-mode"></a>使用 COM + 裝載模式從介面新增特定方法

- 請使用包含必要方法之明確命名的 `/install` 和 `/hosting:complus` 選項來執行 ComSvcConfig，如下列範例所示。

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose
    ```

     此命令只會將來自 `Credit` 介面的 `Debit` 和 `IFinances` 方法當成作業新增至公開的服務合約中。 介面上的其他所有方法都會從合約中省略，而且無法透過 Web 服務用戶端來呼叫。

## <a name="add-an-interface-using-the-web-hosting-mode"></a>使用虛擬主機模式新增介面

- 請使用 `/install` 選項和 `/hosting:was` 選項來執行 ComSvcConfig，如下列範例所示。

    ```console
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose
    ```

     此命令會將 `IStockLevels` 元件上的 `ItemInventory.Warehouse` 介面 (來自 OnlineWarehouse COM+ 應用程式) 新增至即將公開為 Web 服務的介面集合。 此服務是由 Web 裝載到 IIS (而不是 COM+) 的 OnlineWarehouse 虛擬目錄，因此必要時會自動啟動應用程式。

     若要使用 Web 裝載的同處理序組態，必須將 COM+ 應用程式設定為透過元件服務系統管理主控台，並以程式庫應用程式身分，而不是以伺服器應用程式身分來執行。 設定為伺服器應用程式身分的應用程式會使用標準 Web 裝載模式，並產生處理序躍點來處理每項要求。

     `/mex` 選項會新增使用相同傳輸的額外中繼資料交換 (MEX) 服務做為應用程式服務端點，以支援想要從服務中擷取合約定義的用戶端。

## <a name="remove-a-web-service-for-a-specified-interface"></a>移除指定之介面的 Web 服務

- 請使用 `/uninstall` 選項來執行 ComSvcConfig，如下列範例所示。

    ```console
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus
    ```

     此命令會移除 `IFinances` 元件的 `ItemOrders.Financial` 介面 (來自 OnlineStore COM+ 應用程式)。

## <a name="list-currently-exposed-interfaces"></a>列出目前公開的介面

- 請使用 `/list` 選項來執行 ComSvcConfig，如下列範例所示。

    ```console
    ComSvcConfig.exe /list
    ```

     此命令會列出限定於本機電腦範圍內，目前公開的介面以及對應的位址與繫結詳細資訊。

## <a name="list-specific-currently-exposed-interfaces"></a>列出特定目前公開的介面

- 請使用 `/list` 選項來執行 ComSvcConfig，如下列範例所示。

    ```console
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus
    ```

     此命令會列出本機電腦上 OnlineStore COM+ 應用程式目前公開的 COM+ 裝載介面，以及對應的位址與繫結詳細資訊。

## <a name="display-help-for-options"></a>顯示選項的說明

- 請使用 /? 選項來執行 ComSvcConfig， 如下列範例所示。

    ```console
    ComSvcConfig.exe /?
    ```

## <a name="see-also"></a>另請參閱

- [與 COM + 應用程式整合總覽](integrating-with-com-plus-applications-overview.md)
