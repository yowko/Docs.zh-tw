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
ms.openlocfilehash: bb8379776066802277886b54c60c502ad58768e0
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748163"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="508ad-102">HOW TO：建立有便捷鍵和自動換行的控制項</span><span class="sxs-lookup"><span data-stu-id="508ad-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="508ad-103">此範例示範如何建立具有便捷鍵並支援自動換行的控制項。</span><span class="sxs-lookup"><span data-stu-id="508ad-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="508ad-104">此範例會使用<xref:System.Windows.Controls.Label>來說明這些概念的控制項。</span><span class="sxs-lookup"><span data-stu-id="508ad-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="508ad-105">範例</span><span class="sxs-lookup"><span data-stu-id="508ad-105">Example</span></span>  
 <span data-ttu-id="508ad-106">**將自動換行功能新增到您的標籤**</span><span class="sxs-lookup"><span data-stu-id="508ad-106">**Add Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="508ad-107"><xref:System.Windows.Controls.Label>控制項不支援文字換行。</span><span class="sxs-lookup"><span data-stu-id="508ad-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="508ad-108">如果您需要一個多行換行的標籤，您可以將支援自動換行的另一個元素內嵌在巢狀結構中，並將該元素放在標籤內。</span><span class="sxs-lookup"><span data-stu-id="508ad-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="508ad-109">下列範例示範如何使用<xref:System.Windows.Controls.TextBlock>讓會包裝數行文字的標籤。</span><span class="sxs-lookup"><span data-stu-id="508ad-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 <span data-ttu-id="508ad-110">**將便捷鍵和自動換行功能新增到您的標籤**</span><span class="sxs-lookup"><span data-stu-id="508ad-110">**Add an Access Key and Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="508ad-111">如果您需要<xref:System.Windows.Controls.Label>具有便捷鍵 （助憶鍵），請使用<xref:System.Windows.Controls.AccessText>內的項目<xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="508ad-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="508ad-112">控制這類<xref:System.Windows.Controls.Label>， <xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.RadioButton>， <xref:System.Windows.Controls.CheckBox>， <xref:System.Windows.Controls.MenuItem>， <xref:System.Windows.Controls.TabItem>， <xref:System.Windows.Controls.Expander>，以及<xref:System.Windows.Controls.GroupBox>有預設控制項範本。</span><span class="sxs-lookup"><span data-stu-id="508ad-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="508ad-113">這些範本包含<xref:System.Windows.Controls.ContentPresenter>。</span><span class="sxs-lookup"><span data-stu-id="508ad-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="508ad-114">您可以設定的屬性之一<xref:System.Windows.Controls.ContentPresenter>是<xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true"，可用來指定控制項的便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="508ad-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="508ad-115">下列範例示範如何建立<xref:System.Windows.Controls.Label>，具有便捷鍵，並支援文字換行。</span><span class="sxs-lookup"><span data-stu-id="508ad-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="508ad-116">若要啟用文字換行，範例會設定<xref:System.Windows.Controls.AccessText.TextWrapping%2A>屬性，並使用底線字元來指定存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="508ad-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="508ad-117">(緊接在底線字元之後的字元就是便捷鍵)。</span><span class="sxs-lookup"><span data-stu-id="508ad-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="508ad-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="508ad-118">See also</span></span>
- <span data-ttu-id="508ad-119">[如何：設定標籤的目標屬性](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752101(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="508ad-119">[How to: Set the Target Property of a Label](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752101(v=vs.90))</span></span>
