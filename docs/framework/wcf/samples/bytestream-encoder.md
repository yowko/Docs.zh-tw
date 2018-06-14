---
title: ByteStream 編碼器
ms.date: 03/30/2017
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
ms.openlocfilehash: ab9ccf47527dcf7f01f272f09b3b341d30fbd8d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499676"
---
# <a name="bytestream-encoder"></a>ByteStream 編碼器
這個範例示範如何建立 `ByteStreamHttpBinding`，也就是示範位元組資料流編碼器功能的 <xref:System.ServiceModel.Channels.Binding>。  
  
## <a name="discussion"></a>討論  
 這個範例示範如何使用標準的繫結項目 <xref:System.ServiceModel.Channels.Binding> 和 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> 建立標準的 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>。 這個範例示範如何使用位元組資料流編碼器上傳和下載影像。 位元組資料流編碼器功能僅支援 HTTP 傳輸，並不支援可靠的訊息處理 (Reliable Messaging) 或安全性這類功能。 唯一支援的 <xref:System.ServiceModel.Channels.MessageVersion> 是 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。  
  
> [!IMPORTANT]
>  如果您是在 [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] 或 [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)] 中執行這個範例，請確定您是以更高的權限執行 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟 [ByteStreamHttpBinding.sln] 檔案。  
  
2.  啟動 ByteStreamHttpBindingServer 專案的新執行個體，以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取**偵錯**，然後**開始新執行個體**從內容功能表。  
  
3.  啟動 ByteStreamHttpBindingClient 專案的新執行個體，以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取**偵錯**，**開始新執行個體**從內容功能表。
