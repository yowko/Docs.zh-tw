---
title: HOW TO：將自訂資料加入至筆墨資料
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: c524e30943a21426e2e5e8fe6ae009999924fead
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361664"
---
# <a name="how-to-add-custom-data-to-ink-data"></a>HOW TO：將自訂資料加入至筆墨資料
您可以將自訂資料加入時，筆墨會儲存成筆墨序列化格式 (ISF) 將儲存的筆墨。  您可以自訂將資料儲存到<xref:System.Windows.Ink.DrawingAttributes>，則<xref:System.Windows.Ink.StrokeCollection>，或<xref:System.Windows.Ink.Stroke>。  能夠將自訂的資料儲存在三個物件上，讓您能夠決定最佳的位置來儲存資料。  所有三個類別會使用類似的方法，來儲存及存取自訂的資料。  
  
 只有下列類型可以儲存為自訂的資料：  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Boolean>[]  
  
-   <xref:System.Byte>  
  
-   <xref:System.Byte>[]  
  
-   <xref:System.Char>  
  
-   <xref:System.Char>[]  
  
-   <xref:System.DateTime>  
  
-   <xref:System.DateTime>[]  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Decimal>[]  
  
-   <xref:System.Double>  
  
-   <xref:System.Double>[]  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int16>[]  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int32>[]  
  
-   <xref:System.Int64>  
  
-   <xref:System.Int64>[]  
  
-   <xref:System.Single>  
  
-   <xref:System.Single>[]  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <xref:System.UInt16>[]  
  
-   <xref:System.UInt32>  
  
-   <xref:System.UInt32>[]  
  
-   <xref:System.UInt64>  
  
-   <xref:System.UInt64>[]  
  
## <a name="example"></a>範例  
 下列範例示範如何新增和擷取自訂的資料，從<xref:System.Windows.Ink.StrokeCollection>。  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 下列範例會建立應用程式，顯示<xref:System.Windows.Controls.InkCanvas>和兩個按鈕。  [] 按鈕， `switchAuthor`，可讓兩個不同的作者所使用的兩種筆。  [] 按鈕`changePenColors`上變更的每個筆劃色彩<xref:System.Windows.Controls.InkCanvas>根據作者。  應用程式會定義兩個<xref:System.Windows.Ink.DrawingAttributes>物件，並將自訂屬性加入至作者所繪製的圖會指出每個<xref:System.Windows.Ink.Stroke>。  當使用者按一下`changePenColors`，應用程式的自訂屬性的值根據筆劃的外觀會變更。  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
