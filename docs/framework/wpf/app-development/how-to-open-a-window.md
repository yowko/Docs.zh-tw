---
title: "如何： 開啟視窗"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6f3efda8257d9f7ed843438b0e9fb42e13de2c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-window"></a>如何： 開啟視窗
這個範例示範如何開啟視窗。  
  
## <a name="example"></a>範例  
 藉由執行個體化開啟的視窗<xref:System.Windows.Window>，然後呼叫<xref:System.Windows.Window.Show%2A>方法。 <xref:System.Windows.Window.Show%2A>會開啟視窗並立即傳回而不等候新的視窗關閉。 這類視窗就是所謂*非強制回應*視窗中，並不會限制使用者輸入。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 具現化<xref:System.Windows.Window>需要呼叫不安全的原生方法的權限 (請參閱<xref:System.Windows.Window.%23ctor%2A>)。
