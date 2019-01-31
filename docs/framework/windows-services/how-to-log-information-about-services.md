---
title: HOW TO：記錄關於服務的資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
author: ghogen
ms.openlocfilehash: ff3eb0dd27f097899fc19f57142034ffd2bb382a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660134"
---
# <a name="how-to-log-information-about-services"></a>HOW TO：記錄關於服務的資訊
根據預設，所有的 Windows 服務專案都能與應用程式事件記錄檔互動，並在其中寫入資訊和例外狀況。 您使用 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性來表示在您的應用程式中是否要這項功能。 根據預設，會為您以 Windows 服務專案範本建立任何服務開啟記錄。 您可以使用靜態形式的 <xref:System.Diagnostics.EventLog> 類別將服務資訊寫入記錄檔，而不需要建立 <xref:System.Diagnostics.EventLog> 元件的執行個體或手動註冊來源。  
  
 您的服務安裝程式會自動在專案中註冊每個服務，做為開啟記錄功能時，服務安裝所在電腦上的應用程式記錄檔的有效事件來源。 服務會在每次服務啟動、停止、暫停、繼續、安裝或解除安裝時記錄資訊。 它也會記錄發生的任何失敗。 使用預設行為時，您不需要撰寫任何程式碼，以將項目寫入記錄檔；服務會自動為您處理。  
  
 如果您想要寫入應用程式記錄檔以外的事件記錄檔，您必須將 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性設為 `false`、在您的服務程式碼內建立自己的自訂事件記錄檔，然後將您的服務註冊為該記錄檔項目的有效來源。 接著，您必須撰寫程式碼，每當您感興趣的動作發生時，就將項目記錄至記錄檔。  
  
> [!NOTE]
>  如果您使用自訂的事件記錄檔，並設定服務應用程式寫入其中，則在您的程式碼中設定服務的 <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 屬性之前，不得嘗試存取事件記錄檔。 事件記錄檔需要此屬性的值才能將您的服務註冊為有效的事件來源。  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>啟用服務的預設事件記錄  
  
-   將您的元件 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性設為 `true`。  
  
    > [!NOTE]
    >  根據預設，這個屬性設定為 `true`。 您不需要明確地設定這個屬性，除非您正在建置更複雜的處理，例如評估條件，然後根據該條件的結果設定 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性。  
  
### <a name="to-disable-event-logging-for-your-service"></a>停用服務的事件記錄  
  
-   將您的元件 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性設為 `false`。  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>設定記錄至自訂的記錄檔  
  
1.  將 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性設定為 `false`。  
  
    > [!NOTE]
    >  您必須將 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 設為 false 以使用自訂的記錄檔。  
  
2.  在 Windows 服務應用程式中，設定 <xref:System.Diagnostics.EventLog> 元件的執行個體。  
  
3.  藉由呼叫 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> 方法並指定來源字串和您要建立之記錄檔的名稱，建立自訂的記錄檔。  
  
4.  將 <xref:System.Diagnostics.EventLog.Source%2A> 元件執行個體上的 <xref:System.Diagnostics.EventLog> 屬性設為您在步驟 3 中建立的來源字串。  
  
5.  藉由存取 <xref:System.Diagnostics.EventLog.WriteEntry%2A> 元件執行個體上的 <xref:System.Diagnostics.EventLog> 方法，撰寫您的項目。  
  
     下列程式碼示範如何設定記錄至自訂的記錄檔。  
  
    > [!NOTE]
    >  在此程式碼範例中， <xref:System.Diagnostics.EventLog> 元件的執行個體命名為 `eventLog1` (在 Visual Basic 中為`EventLog1` )。 如果您在步驟 2 中以另一個名稱建立執行個體，請跟著變更程式碼。  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>另請參閱
- [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
