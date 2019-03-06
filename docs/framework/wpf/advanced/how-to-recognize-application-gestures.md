---
title: 如何：辨認應用程式筆勢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
ms.openlocfilehash: 99deaa528a089f2d16268747f2e946873f3420a0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370510"
---
# <a name="how-to-recognize-application-gestures"></a>如何：辨認應用程式筆勢
下列範例示範如何清除的筆墨，當使用者提出<xref:System.Windows.Ink.ApplicationGesture.ScratchOut>軌跡上<xref:System.Windows.Controls.InkCanvas>。 這個範例假設<xref:System.Windows.Controls.InkCanvas>，稱為`inkCanvas1`，在 XAML 檔案中宣告。  
  
## <a name="example"></a>範例  
 [!code-csharp[HowToRecognizeGestures#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Ink.ApplicationGesture>
- <xref:System.Windows.Controls.InkCanvas>
- <xref:System.Windows.Controls.InkCanvas.Gesture>
