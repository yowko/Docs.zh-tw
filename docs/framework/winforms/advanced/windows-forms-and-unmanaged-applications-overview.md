---
title: "Windows Form 和 Unmanaged 應用程式概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop
- ActiveX controls [Windows Forms], about ActiveX controls
- Windows Forms, interop
ms.assetid: 0a26d99d-8135-4895-8760-c9a2b5f67f14
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ad64588727584a9b3de0a95e9bad252a3fb0581
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Windows Form 和 Unmanaged 應用程式概觀
伴隨著某些注意事項，Windows Form 應用程式和控制項能與 Unmanaged 應用程式交互操作。 下列各節描述 Windows Form 應用程式和控制項支援及不支援的案例和組態。  
  
## <a name="windows-forms-controls-and-activex-applications"></a>Windows Form 控制項和 ActiveX 應用程式  
 在設計來裝載 ActiveX 控制項的應用程式中不支援 Windows Form 控制項，但 Microsoft Internet Explorer 和 Microsoft Foundation Classes (MFC) 例外。 其他能夠裝載 ActiveX 控制項的應用程式和開發工具，包含早於 Visual Studio .NET 2003 的 Visual Studio 版本之 ActiveX 測試容器，並不支援裝載 Windows Form 控制項。  
  
 這些條件約束也適用於透過元件物件模型 COM Interop 使用 Windows Form 控制項時。 只在 Internet Explorer 中支援透過 COM 可呼叫包裝函式 (CCW) 使用 Windows Form 控制項。 如需 COM Interop的詳細資訊，請參閱  
  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md).  
  
 下表顯示對於 Windows Form 控制項可用的 ActiveX 裝載支援。  
  
|Windows Form 版本|支援|  
|---------------------------|-------------|  
|.NET Framework 1.0 版|Internet Explorer 5.01 和更新版本|  
|.NET Framework 1.1 和更新版本|Internet Explorer 5.01 和更新版本<br /><br /> Microsoft Foundation Classes (MFC) 7.0 和更新版本|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>裝載 Windows Form 元件做為 ActiveX 控制項  
 在 .NET Framework 1.1，已擴充包含 MFC 7.0 和更新版本的支援。 這項支援包含任何與 MFC 7.0 和更新版本 ActiveX 控制項容器完全相容的容器。  
  
 不過，這並不支援登錄 Windows Form 控制項為 ActiveX 控制項。 此外，不支援呼叫 Windows Form 控制項的 `com.ms.win32.Ole32.CoCreateInstance` 方法。 僅支援 Windows Form 控制項的 Managed 啟用。 一旦您建立 Windows Form 控制項，您就可以將它裝載於 MFC 應用程式中，如同 ActiveX 控制項。  
  
 若要在 Unmanaged 應用程式中使用 Windows Form 控制項，您必須使用 Unmanaged 的 CLR 裝載應用程式開發介面，或使用 C++ Interop 功能來裝載 CLR。 使用 C++ Interop 功能是建議的解決方案。  
  
## <a name="windows-forms-in-com-client-applications"></a>COM 用戶端應用程式中的 Windows Form  
 當您從 COM 用戶端應用程式中開啟 Windows Form，例如從 Visual Basic 6.0 應用程式或 MFC 應用程式中開啟，則表單可能會發生未預期的狀況。 例如，當您按 TAB 鍵時，焦點不會從一個控制項變更到另一個控制項。 當焦點在命令按鈕的時候，當您按 ENTER 鍵，則不會引發按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。 您也可能會遇到按鍵或滑鼠活動未預期的行為。  
  
 因為 Unmanaged 應用程式不會實作 Windows Form 正常運作所需的訊息迴圈支援，所以會發生這種行為。 COM 用戶端應用程式所提供的訊息迴圈本質上不同於 Windows Form 訊息迴圈。  
  
 應用程式的訊息迴圈是一種內部程式迴圈，它從執行緒訊息佇列擷取訊息並轉譯，然後傳送到應用程式以進行處理。 Windows Form 訊息迴圈不具有和舊版應用程式 (例如 Visual Basic 6.0 應用程式和 MFC 應用程式) 提供的訊息迴圈相同的架構。 張貼至訊息迴圈的視窗訊息可能以和 Windows Form 所預期的不同方式處理。 因此，可能會發生未預期的行為。 某些按鍵組合可能無法運作，或是某些滑鼠活動可能無法運作，或者可能不會如預期般引發某些事件。  
  
## <a name="resolving-interoperability-issues"></a>解決互通性問題  
 藉由顯示使用 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> 方法建立之 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 訊息迴圈上的表單，您可解決這些問題。  
  
 若要讓 Windows Form 在 COM 用戶端應用程式正確運作，您必須在 Windows Form 訊息迴圈上執行。 若要執行此工作，請使用下列的其中一個方法：  
  
-   使用 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法，以顯示 Windows Form。 如需詳細資訊，請參閱[如何：顯示 Windows Form 和 ShowDialog 方法以支援 COM Interop](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)。  
  
-   在新的執行緒上顯示每個 Windows Form。 如需詳細資訊，請參閱[如何：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)。  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 和 Unmanaged 應用程式](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 [.NET Framework 應用程式中的 COM 互通性](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [COM 互通性範例](http://msdn.microsoft.com/library/09c38567-6380-4d70-848a-e896a4ca05f4)  
 [Aximp.exe (Windows Forms ActiveX 控制項匯入工具)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 [將 .NET Framework 元件公開給 COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [封裝 COM 的組件](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [向 COM 註冊組件](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [操作說明：顯示 Windows Forms 和 ShowDialog 方法以支援 COM Interop](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
