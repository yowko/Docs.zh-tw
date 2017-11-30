---
title: "如何：以程式設計方式撰寫服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 1721417b8d1fc799e6af5d09762ee852d9fbfb03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-services-programmatically"></a>如何：以程式設計方式撰寫服務
如果您選擇不使用 Windows 服務專案範本，您可以藉由建立繼承和其他基礎結構項目自行撰寫您自己的服務。 當您以程式設計方式建立服務時，您必須執行幾個範本會為您處理的步驟：  
  
-   您必須設定您的服務類別繼承自<xref:System.ServiceProcess.ServiceBase>類別。  
  
-   您必須建立`Main`方式，讓您定義要執行的服務的服務專案並呼叫<xref:System.ServiceProcess.ServiceBase.Run%2A>在其上的方法。  
  
-   您必須覆寫<xref:System.ServiceProcess.ServiceBase.OnStart%2A>和<xref:System.ServiceProcess.ServiceBase.OnStop%2A>程序和任何程式碼中的填滿您希望他們執行。  
  
### <a name="to-write-a-service-programmatically"></a>以程式設計方式撰寫服務  
  
1.  建立空白的專案，並建立必要的命名空間的參考，依照下列步驟：  
  
    1.  在**方案總管 中**，以滑鼠右鍵按一下**參考**節點，然後按一下**加入參考**。  
  
    2.  在**.NET Framework**索引標籤上，捲動到**System.dll**按一下**選取**。  
  
    3.  捲動到**System.ServiceProcess.dll**按一下**選取**。  
  
    4.  按一下 [確定]。  
  
2.  加入類別，並將它設定為繼承自<xref:System.ServiceProcess.ServiceBase>:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  加入下列程式碼來設定您的服務類別：  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  建立`Main`方法，為您的類別，並用它來定義的服務將會包含您的類別。`userService1`是類別的名稱：  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  覆寫<xref:System.ServiceProcess.ServiceBase.OnStart%2A>方法，並定義您想要啟動您的服務時，會發生任何的處理。  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  覆寫您想要定義自訂處理，其他任何的方法，並撰寫程式碼來判斷服務應該在每個案例所採取的動作。  
  
7.  為服務應用程式加入必要的安裝程式。 如需詳細資訊，請參閱[如何： 加入至您的服務應用程式的安裝程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
8.  建置您的專案選取**建置方案**從**建置**功能表。  
  
    > [!NOTE]
    >  請勿按 F5 執行您的專案，您無法透過這個方法來執行服務專案。  
  
9. 建立安裝專案和自訂動作來安裝您的服務。 如需範例，請參閱[逐步解說： 在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。  
  
10. 安裝服務。 如需詳細資訊，請參閱 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [如何： 建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [如何： 加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [如何： 記錄服務的相關資訊](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [逐步解說： 在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
