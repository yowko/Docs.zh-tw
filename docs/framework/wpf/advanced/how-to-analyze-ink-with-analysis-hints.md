---
title: 如何：以分析提示分析筆墨
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], analyzing
- analyzing ink [WPF]
- ink [WPF], AnalysisHintNode objects [WPF]
- AnalysisHintNode objects [WPF]
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
ms.openlocfilehash: 74f8b3df5767888e8bca0d9f67e9c47630353fb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543598"
---
# <a name="how-to-analyze-ink-with-analysis-hints"></a><span data-ttu-id="4f2ed-102">如何：以分析提示分析筆墨</span><span class="sxs-lookup"><span data-stu-id="4f2ed-102">How to: Analyze Ink with Analysis Hints</span></span>
<span data-ttu-id="4f2ed-103">[System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx)提供提示[System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx)它附加。</span><span class="sxs-lookup"><span data-stu-id="4f2ed-103">An [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) provides a hint for the [System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) to which it is attached.</span></span>  <span data-ttu-id="4f2ed-104">提示可套用至所指定的區域[System.Windows.Ink.ContextNode.Location%2A](https://msdn.microsoft.com/library/system.windows.ink.contextnode.location(v=vs.100).aspx)屬性[System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) ，並提供額外的內容以筆墨分析器增進辨識準確度。</span><span class="sxs-lookup"><span data-stu-id="4f2ed-104">The hint applies to the area specified by the [System.Windows.Ink.ContextNode.Location%2A](https://msdn.microsoft.com/library/system.windows.ink.contextnode.location(v=vs.100).aspx) property of the [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) and provides extra context to the ink analyzer to improve recognition accuracy.</span></span> <span data-ttu-id="4f2ed-105">[System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx)分析筆墨從取得的提示區域內時，適用於此內容資訊。</span><span class="sxs-lookup"><span data-stu-id="4f2ed-105">The [System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) applies this context information when analyzing ink obtained from within the hint's area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f2ed-106">範例</span><span class="sxs-lookup"><span data-stu-id="4f2ed-106">Example</span></span>  
 <span data-ttu-id="4f2ed-107">下列範例會使用多個應用程式[System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx)接受筆跡輸入在表單上的物件。</span><span class="sxs-lookup"><span data-stu-id="4f2ed-107">The following example is an application that uses multiple [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) objects on a form that accepts ink input.</span></span> <span data-ttu-id="4f2ed-108">應用程式使用[System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode.factoid(v=vs.100))屬性在表單上提供內容資訊的每個項目。</span><span class="sxs-lookup"><span data-stu-id="4f2ed-108">The application uses the [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode.factoid(v=vs.100)) property to provide context information for each entry on the form.</span></span>  <span data-ttu-id="4f2ed-109">應用程式會使用背景分析來分析筆墨，並清除所有筆墨形式使用者停止新增筆跡之後的五秒。</span><span class="sxs-lookup"><span data-stu-id="4f2ed-109">The application uses background analysis to analyze the ink and clears the form of all ink five seconds after the user stops adding ink.</span></span>  
  
 [!code-xaml[HowToAnalyzeInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]
