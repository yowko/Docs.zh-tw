---
title: 使用圖形容器
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: cfad7254057a31ea8268784cd4b6849850f3e2aa
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704461"
---
# <a name="using-graphics-containers"></a>使用圖形容器
A<xref:System.Drawing.Graphics>物件提供方法，例如<xref:System.Drawing.Graphics.DrawLine%2A>， <xref:System.Drawing.Graphics.DrawImage%2A>，和<xref:System.Drawing.Graphics.DrawString%2A>向量影像、 點陣影像和文字顯示。 A<xref:System.Drawing.Graphics>物件也有數個屬性影響的品質和方向繪製的項目。 比方說，平滑的模式屬性會決定是否消除鋸齒套用至直線和曲線，以及全局轉換屬性影響的位置和旋轉所繪製的項目。  
  
 A<xref:System.Drawing.Graphics>物件是特定顯示裝置與相關聯。 當您使用<xref:System.Drawing.Graphics>物件，以在視窗中，繪製<xref:System.Drawing.Graphics>物件也是該特定視窗相關聯。  
  
 A<xref:System.Drawing.Graphics>物件可以視為作為容器因為它包含一組會影響繪圖的屬性並將它連結至裝置特定資訊。 您可以建立次要的容器內的現有<xref:System.Drawing.Graphics>藉由呼叫物件<xref:System.Drawing.Graphics.BeginContainer%2A>方法，<xref:System.Drawing.Graphics>物件。  
  
## <a name="in-this-section"></a>本節內容  
 [管理圖形物件的狀態](managing-the-state-of-a-graphics-object.md)  
 描述如何在管理品質設定、 裁剪區域和轉換<xref:System.Drawing.Graphics>物件。  
  
 [使用巢狀圖形容器](using-nested-graphics-containers.md)  
 示範如何使用容器來控制的狀態<xref:System.Drawing.Graphics>物件。
