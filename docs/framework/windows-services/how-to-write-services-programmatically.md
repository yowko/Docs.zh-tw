---
title: "如何：以程式設計方式撰寫服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "服務, 建立"
  - "Windows 服務應用程式, 建立"
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
caps.latest.revision: 21
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 21
---
# 如何：以程式設計方式撰寫服務
如果您選擇不使用 Windows 服務專案範本，您也可以藉由設定繼承 \(Inheritance\) 和其他基礎結構項目撰寫自己的服務。  當您以程式設計方式建立服務時，必須執行範本會為您處理的幾個步驟：  
  
-   您必須設定要繼承自 <xref:System.ServiceProcess.ServiceBase> 類別的服務類別。  
  
-   您必須為用來定義要執行之服務的服務專案建立 `Main` 方法，並在服務上呼叫 <xref:System.ServiceProcess.ServiceBase.Run%2A> 方法。  
  
-   您必須覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 程序，並填入要執行的程式碼。  
  
### 若要以程式設計方式撰寫服務  
  
1.  建立空白專案，並遵循以下步驟，建立必要命名空間的參考：  
  
    1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**參考**\] 節點，然後按一下 \[**加入參考**\]。  
  
    2.  在 \[**.NET Framework**\] 索引標籤上，捲動到 \[**System.dll**\]，並按一下 \[**選取**\]。  
  
    3.  捲動到 \[**System.ServiceProcess.dll**\]，並按一下 \[**選取**\]。  
  
    4.  按一下 \[**確定**\]。  
  
2.  加入類別，並將它設定為繼承自 <xref:System.ServiceProcess.ServiceBase>：  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  加入下列程式碼來設定服務類別：  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  建立類別的 `Main` 方法，並使用它定義類別包含的服務，`userService1` 為類別的名稱：  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法，並定義服務啟動時要執行的處理。  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  覆寫其他您希望定義自訂處理的任何方法，並撰寫程式碼來決定服務在每一種情況下應採取的動作。  
  
7.  為服務應用程式加入必要的安裝程式。  如需詳細資訊，請參閱[如何：加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
8.  從 \[**建置**\] 功能表中選取 \[**建置方案**\]，建置您的專案。  
  
    > [!NOTE]
    >  請勿按 F5 執行專案，因為您無法以這種方式執行服務專案。  
  
9. 建立安裝專案和自訂動作來安裝您的服務。  如需範例，請參閱[逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。  
  
10. 安裝服務。  如需詳細資訊，請參閱[如何：安裝及解除安裝服務](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)。  
  
## 請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)   
 [如何：加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)   
 [如何：記錄關於服務的資訊](../../../docs/framework/windows-services/how-to-log-information-about-services.md)   
 [逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)