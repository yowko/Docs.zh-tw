---
title: "如何：在 Windows Form 上建立簡單繫結控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 887f5cd89e52cf91c4e18fab5c97f82cba9a5b85
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>如何：在 Windows Form 上建立簡單繫結控制項
與*簡單繫結*，您可以在控制項中顯示單一資料元素，例如資料集資料表中的資料行值。 您可以簡單繫結控制項的任何屬性的資料值。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-simple-bind-a-control"></a>以簡單繫結控制項  
  
1.  連接至資料來源。 如需詳細資訊，請參閱[連接到資料來源](../../../docs/framework/data/adonet/connecting-to-a-data-source.md)。  
  
2.  在表單中，選取控制項，並顯示**屬性**視窗。  
  
3.  展開**(DataBindings)**屬性。  
  
     最常繫結的屬性會顯示下面**(DataBindings)**屬性。 例如，在大多數的控制項，**文字**屬性最常繫結。  
  
4.  如果您想要將屬性繫結不是其中一個常見的繫結的屬性，請按一下**省略**按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 在**（進階）**方塊，即可顯示**格式化與進階繫結**該控制項屬性 對話方塊的完整清單。  
  
5.  選取您想要繫結，並按一下底下的下拉式箭頭的屬性**繫結**。  
  
     會顯示可用資料來源清單。  
  
6.  展開您想要繫結的資料來源，直到您找到您要的單一資料項目。 例如，如果您要在資料集資料表中繫結資料行值，展開資料集的名稱，然後展開資料表名稱來顯示資料行名稱。  
  
7.  按一下要繫結項目的名稱。  
  
8.  如果您在**格式化與進階繫結**對話方塊中，按一下 **確定**返回**屬性**視窗。  
  
9. 如果您想要繫結控制項的其他屬性，重複步驟 3 到 7。  
  
    > [!NOTE]
    >  因為簡單繫結控制項顯示單一資料元素，所以經常包含在 Windows Form 和簡單繫結控制項中的巡覽邏輯。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Binding>  
 [Windows Forms 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [資料繫結和 Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
