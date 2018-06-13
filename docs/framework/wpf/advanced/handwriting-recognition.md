---
title: 手寫辨識
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
ms.openlocfilehash: d72d8b42a23205d8599b23a467677dd2f05d5cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542372"
---
# <a name="handwriting-recognition"></a><span data-ttu-id="a6f9d-102">手寫辨識</span><span class="sxs-lookup"><span data-stu-id="a6f9d-102">Handwriting Recognition</span></span>
<span data-ttu-id="a6f9d-103">本節討論有關 WPF 平台中數位筆跡的辨識基本概念。</span><span class="sxs-lookup"><span data-stu-id="a6f9d-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="a6f9d-104">辨識方案</span><span class="sxs-lookup"><span data-stu-id="a6f9d-104">Recognition Solutions</span></span>  
 <span data-ttu-id="a6f9d-105">下列範例示範如何使用 [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) 類別來辨識筆跡。</span><span class="sxs-lookup"><span data-stu-id="a6f9d-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6f9d-106">此範例需要在系統上安裝手寫辨識器。</span><span class="sxs-lookup"><span data-stu-id="a6f9d-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="a6f9d-107">在 Visual Studio 中，建立稱為 **InkRecognition** 的新 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="a6f9d-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="a6f9d-108">將 Window1.xaml 檔案的內容取代為下列 XAML 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a6f9d-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="a6f9d-109">此程式碼會轉譯應用程式的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="a6f9d-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="a6f9d-110">新增可在 \Program Files\Common Files\Microsoft Shared\Ink 中找到之 Microsoft Ink 組件的參考 (Microsoft.Ink.dll)。</span><span class="sxs-lookup"><span data-stu-id="a6f9d-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="a6f9d-111">將程式碼後置檔案的內容取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="a6f9d-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a6f9d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6f9d-112">See Also</span></span>  
 <span data-ttu-id="a6f9d-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a6f9d-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span></span>
