---
title: "Windows Form 和 Unmanaged 應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2672e8f87b28e81a9aa233cbf0f1b2c24b2239c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows Form 和 Unmanaged 應用程式
伴隨著某些注意事項，Windows Form 應用程式和控制項能與 Unmanaged 應用程式交互操作。 下列各節描述 Windows Form 應用程式和控制項支援及不支援的案例和組態。  
  
## <a name="in-this-section"></a>本節內容  
 [Windows Forms 和 Unmanaged 應用程式概觀](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 針對如何使用及實作 Windows Form 控制項來與 Unmanaged 應用程式搭配運作，提供一般相關資訊。  
  
 [操作說明：顯示 Windows Forms 和 ShowDialog 方法以支援 COM Interop](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 提供程式碼範例，示範如何使用 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法，在 Unmanaged 應用程式中執行 Windows Form。  
  
 [How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 提供程式碼範例，示範如何讓 Windows Form 在其自己的執行緒上執行。  
  
 另請參閱 [逐步解說：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop](http://msdn.microsoft.com/library/ms233639\(v=vs.110\))。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 用來為 Windows Form 建立個別的執行緒。  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 為執行緒啟動訊息迴圈。  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 將呼叫從 Unmanaged 應用程式封送處理至表單。  
  
## <a name="related-sections"></a>相關章節  
 [將 .NET Framework 元件公開給 COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 針對如何在 Unmanaged 應用程式中使用 .NET Framework 類型，提供一般相關資訊。
