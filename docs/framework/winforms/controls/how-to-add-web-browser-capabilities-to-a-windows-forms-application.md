---
title: 如何：將 Web 瀏覽器功能加入至 Windows Forms 應用程式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3e7cde23c7395e778f8f6cf9b13f998dded18d69
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>如何：將 Web 瀏覽器功能加入至 Windows Forms 應用程式
利用 <xref:System.Windows.Forms.WebBrowser> 控制項，您可以將 Web 瀏覽器功能加入應用程式。 根據預設，此控制項的作用類似 Web 瀏覽器。 設定 <xref:System.Windows.Forms.WebBrowser.Url%2A> 屬性來載入初始 URL 之後，您可以按一下超連結或使用鍵盤快速鍵來巡覽，在巡覽歷程記錄中前後移動。 根據預設，您可以透過滑鼠右鍵捷徑功能表來存取其他瀏覽器功能。 您也可以將新文件拖曳至控制項加以開啟。 <xref:System.Windows.Forms.WebBrowser> 控制項也有數個屬性、方法和事件，可讓您用來實作類似 Internet Explorer 中的使用者介面功能。  
  
 下列程式碼範例會實作網址列、一般瀏覽器按鈕、[檔案] 功能表、狀態列，以及可顯示目前頁面標題的標題列。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   `System,``System.Drawing` 和 `System.Windows.Forms` 組件的參考。  
  
 Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.WebBrowser>  
 [WebBrowser 控制項](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
