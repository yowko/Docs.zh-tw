---
title: 如何：使用應用程式範圍的資源字典
description: 瞭解如何在 Windows Presentation Foundation （WPF）中定義和使用應用程式範圍的自訂資源字典。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 9d117dea6c554339b4b462b9bf37b80da2dc477f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613705"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>如何：使用應用程式範圍的資源字典
此範例示範如何定義和使用應用程式範圍自訂資源字典。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Application>公開共用資源的應用程式範圍存放區： <xref:System.Windows.Application.Resources%2A> 。 根據預設， <xref:System.Windows.Application.Resources%2A> 會使用類型的實例來初始化屬性 <xref:System.Windows.ResourceDictionary> 。 當您使用來取得和設定應用程式範圍的屬性時，會使用這個實例 <xref:System.Windows.Application.Resources%2A> 。 如需詳細資訊，請參閱[如何：取得和設定應用程式範圍的資源](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100))。
  
 如果您有使用設定的多個資源 <xref:System.Windows.Application.Resources%2A> ，則可以改為使用自訂資源字典來儲存這些資源，並 <xref:System.Windows.Application.Resources%2A> 改為加以設定。 以下顯示如何使用 XAML 宣告自訂資源字典。
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 使用交換整個資源字典 <xref:System.Windows.Application.Resources%2A> ，可讓您支援應用程式範圍主題，其中每個主題都是由單一資源字典封裝。 下列範例會示範如何設定 <xref:System.Windows.ResourceDictionary>。  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 以下顯示如何從 XAML 中所公開的資源字典取得應用程式範圍的資源 <xref:System.Windows.Application.Resources%2A> 。  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 下列會顯示也可以如何使用程式碼來取得資源。  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 使用時，有兩個要進行的考慮 <xref:System.Windows.Application.Resources%2A> 。 首先，字典索引*鍵*是物件，因此當您設定並取得屬性值時，必須使用完全相同的物件實例。 （請注意，使用字串時，索引鍵會區分大小寫）。第二，字典*值*是物件，因此，您必須在取得屬性值時，將值轉換成所需的類型。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [合併的資源字典](../advanced/merged-resource-dictionaries.md)
