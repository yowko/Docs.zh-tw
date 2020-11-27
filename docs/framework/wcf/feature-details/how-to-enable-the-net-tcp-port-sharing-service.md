---
title: 作法：啟用 Net.TCP 連接埠共用服務
description: 瞭解如何使用 MMC 設定 Net TCP 埠共用服務來啟用 Net.tcp （預設為停用）。
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 7200d82e4a45ce9e36b2a4cec3d0c08e1a5f00ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265462"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>作法：啟用 Net.TCP 連接埠共用服務

Windows Communication Foundation (WCF) 使用稱為 Net.tcp 埠共用服務的 Windows 服務，以加速跨多個進程共用 TCP 埠。 這項服務會安裝為 WCF 的一部分，但預設不會啟用此服務做為安全性預防措施，因此必須在第一次使用之前手動啟用。 本主題說明如何使用 Microsoft Management Console (MMC) 嵌入式管理單元，來設定 Net TCP Port Sharing Service。  
  
 啟用 Net.tcp 埠共用服務並以手動方式啟動之後，請參閱 [如何：設定 WCF 服務使用埠共用](how-to-configure-a-wcf-service-to-use-port-sharing.md) ，以取得如何設定服務以使用此服務的相關資訊。  
  
 如需使用 net.tcp：//埠共用的範例，請參閱 [Net.tcp 埠共用範例](../samples/net-tcp-port-sharing-sample.md)。  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>若要使用 MMC 來啟用 Net.TCP 連接埠共用服務  
  
1. 在 [開始] 功能表中，開啟 [命令提示字元] 視窗並輸入 `services.msc` 或開啟 [執行]，然後 `services.msc` 在 [開啟] 方塊中輸入，以開啟 [服務] 管理主控台。  
  
2. 在服務清單的 [ **名稱** ] 欄中，以滑鼠右鍵按一下 [ **Net.tcp 埠共用服務**]，然後從功能表中選取 [ **屬性** ]。  
  
3. 若要啟用服務的手動啟動，請在 [ **屬性** ] 視窗中選取 [ **一般** ] 索引標籤，然後在 [ **啟動類型** ] 方塊中選取 [手動]， **然後按一下 [** 套用]。  
  
4. 若要啟動服務，請在 [服務狀態] 區域中，按一下 [ **開始** ] 按鈕。 服務狀態現在應該顯示為「已啟動」。  
  
5. 若要返回服務清單，請按一下 [ **確定]**，然後結束 MMC 主控台。  
  
## <a name="example"></a>範例  
  
## <a name="see-also"></a>另請參閱

- [Net.TCP Port Sharing](net-tcp-port-sharing.md)
- [設定 Net.TCP Port Sharing Service](configuring-the-net-tcp-port-sharing-service.md)
