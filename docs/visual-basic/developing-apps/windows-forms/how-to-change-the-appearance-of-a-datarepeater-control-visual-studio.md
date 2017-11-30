---
title: "如何：變更 DataRepeater 控制項的外觀 (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 585ff4c942185f3199fe6e9e47a4ebd9f1f0a478
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>如何：變更 DataRepeater 控制項的外觀 (Visual Studio)
您可以變更的外觀<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在設計階段藉由設定屬性，或在執行階段處理<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件。  
  
 您在設計階段選取控制項的項目範本區段時設定的屬性會針對每個重複<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>在執行階段。 將屬性與外觀相關的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身會顯示在執行階段容器的部分才將處於未涵蓋範圍 (例如，如果<xref:System.Windows.Forms.Control.Padding%2A>屬性設定為較大的值)。  
  
 在執行階段，與外觀相關的屬性可以是根據設定的條件。 例如，在排程的應用程式中，您可能會變更項目過期的項目時，警告使用者的背景色彩。 在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件處理常式，如果您將屬性設定條件陳述式，例如`If…Then`，您也必須使用`Else`子句來指定當不符合條件的外觀。  
  
### <a name="to-change-the-appearance-at-design-time"></a>若要變更設計階段外觀  
  
1.  在 Windows Form 設計工具中，選取的項目範本 （上方） 區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
2.  在 [屬性] 視窗中，選取屬性，變更值。 影響外觀的通用屬性包括<xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.BackgroundImage%2A>， <xref:System.Windows.Forms.Panel.BorderStyle%2A>，和<xref:System.Windows.Forms.Control.ForeColor%2A>。  
  
### <a name="to-change-the-appearance-at-run-time"></a>若要變更執行階段外觀  
  
1.  在 [程式碼編輯器] 中，按一下 [事件] 下拉式清單中的 [DrawItem] 。  
  
2.  在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件處理常式，加入程式碼來設定屬性：  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>範例  
 某些常見的自訂<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項包含替代色彩的方式和變更的色彩為基礎的欄位中顯示資料列。 下列範例會示範如何執行這些自訂項目。 這個範例假設您有<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>繫結至 Northwind 資料庫中的 [產品] 資料表的控制項。  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 請注意，這兩個自訂項目，您必須提供程式碼以設定條件的兩端的屬性。 如果您未指定`Else`條件，您會看到非預期的結果在執行階段。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示未繫結的控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示項目標題](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
