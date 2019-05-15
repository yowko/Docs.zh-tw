---
title: 作法：以程式設計方式撰寫服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: e709db257c839dc7e583412a87af6d25b80de969
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591425"
---
# <a name="how-to-write-services-programmatically"></a>作法：以程式設計方式撰寫服務
如果您選擇不使用 Windows 服務專案範本，則可以藉由自行設定繼承和其他基礎結構元素來撰寫自己的服務。 當您以程式設計方式建立服務時，必須執行範本會為您處理的數個步驟：  
  
- 您必須將服務類別設定為繼承自 <xref:System.ServiceProcess.ServiceBase> 類別。  
  
- 您必須建立服務專案的 `Main` 方法，以定義要執行的服務並在其上呼叫 <xref:System.ServiceProcess.ServiceBase.Run%2A> 方法。  
  
- 您必須覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 程序，並填入任何要執行的程式碼。  
  
### <a name="to-write-a-service-programmatically"></a>以程式設計方式撰寫服務  
  
1. 依照下列步驟來建立空白的專案，並建立必要命名空間的參考：  
  
    1. 在 [方案總管] 中，以滑鼠右鍵按一下 [參考] 節點，然後按一下 [加入參考]。  
  
    2. 在 [.NET Framework] 索引標籤上，捲動到 [System.dll]，然後按一下 [選取]。  
  
    3. 捲動到 [System.ServiceProcess.dll]，然後按一下 [選取]。  
  
    4. 按一下 [確定]。  
  
2. 加入類別，並將它設定為繼承自 <xref:System.ServiceProcess.ServiceBase>：  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. 加入下列程式碼來設定您的服務類別：  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. 為類別建立 `Main` 方法，並使用它來定義類別將包含的服務；`userService1` 是類別的名稱：  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. 覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法，並定義您想要在啟動服務時發生的任何處理。  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. 覆寫您想要定義自訂處理的其他任何方法，並撰寫程式碼來判斷服務應該在每個案例中採取的動作。  
  
7. 為服務應用程式加入必要的安裝程式。 如需詳細資訊，請參閱[如何：將安裝程式新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
8. 從 [建置] 功能表選取 [建置方案]，以建置您的專案。  
  
    > [!NOTE]
    >  請勿按 F5 執行您的專案，您無法透過這個方法來執行服務專案。  
  
9. 建立安裝專案和自訂動作來安裝您的服務。 如需範例，請參閱[逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。  
  
10. 安裝服務。 如需詳細資訊，請參閱[如何：安裝和解除安裝服務](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)。  
  
## <a name="see-also"></a>另請參閱

- [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [如何：將安裝程式新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [如何：記錄關於服務的資訊](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
