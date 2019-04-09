---
title: HOW TO：建立有便捷鍵和自動換行的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: 48e439719afa2426b5d8f822c621080cdc32514e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174040"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a>HOW TO：建立有便捷鍵和自動換行的控制項
此範例示範如何建立具有便捷鍵並支援自動換行的控制項。 此範例會使用<xref:System.Windows.Controls.Label>來說明這些概念的控制項。  
  
## <a name="example"></a>範例  
 **將文字換行新增至您的標籤**  
  
 <xref:System.Windows.Controls.Label>控制項不支援文字換行。 如果您需要一個多行換行的標籤，您可以將支援自動換行的另一個元素內嵌在巢狀結構中，並將該元素放在標籤內。 下列範例示範如何使用<xref:System.Windows.Controls.TextBlock>讓會包裝數行文字的標籤。  
  
 [!code-xaml[LabelSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **將便捷鍵和文字換行新增至您的標籤**  
  
 如果您需要<xref:System.Windows.Controls.Label>具有便捷鍵 （助憶鍵），請使用<xref:System.Windows.Controls.AccessText>內的項目<xref:System.Windows.Controls.Label>。  
  
 控制這類<xref:System.Windows.Controls.Label>， <xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.RadioButton>， <xref:System.Windows.Controls.CheckBox>， <xref:System.Windows.Controls.MenuItem>， <xref:System.Windows.Controls.TabItem>， <xref:System.Windows.Controls.Expander>，以及<xref:System.Windows.Controls.GroupBox>有預設控制項範本。 這些範本包含<xref:System.Windows.Controls.ContentPresenter>。 您可以設定的屬性之一<xref:System.Windows.Controls.ContentPresenter>是<xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true"，可用來指定控制項的便捷鍵。  
  
 下列範例示範如何建立<xref:System.Windows.Controls.Label>，具有便捷鍵，並支援文字換行。 若要啟用文字換行，範例會設定<xref:System.Windows.Controls.AccessText.TextWrapping%2A>屬性，並使用底線字元來指定存取金鑰。 (緊接在底線字元之後的字元就是便捷鍵)。  
  
 [!code-xaml[LabelSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a>另請參閱

- [HOW TO：設定標籤的目標屬性](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752101(v=vs.90))
