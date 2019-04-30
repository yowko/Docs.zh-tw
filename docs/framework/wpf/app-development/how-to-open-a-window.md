---
title: HOW TO：開啟視窗
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 9ce7ffb3f46dd869fda7893745b531bd02d18ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947675"
---
# <a name="how-to-open-a-window"></a>HOW TO：開啟視窗
此範例示範如何開啟視窗。  
  
## <a name="example"></a>範例  
 開啟視窗的方式具現化<xref:System.Windows.Window>，然後呼叫<xref:System.Windows.Window.Show%2A>方法。 <xref:System.Windows.Window.Show%2A> 開啟視窗，並且會立即傳回，而不需等待新的視窗關閉。 這種視窗，也就是*非強制回應* 視窗中，並不會限制使用者輸入。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 具現化<xref:System.Windows.Window>需要權限來呼叫不安全的原生方法 (請參閱<xref:System.Windows.Window.%23ctor%2A>)。
