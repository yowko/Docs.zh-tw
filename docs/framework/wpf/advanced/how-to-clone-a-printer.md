---
title: 如何：複製印表機
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
ms.openlocfilehash: 8f3a9c3b4d9f4bcbe3a6ffcff9868aa7b19b8f28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544192"
---
# <a name="how-to-clone-a-printer"></a><span data-ttu-id="92584-102">如何：複製印表機</span><span class="sxs-lookup"><span data-stu-id="92584-102">How to: Clone a Printer</span></span>
<span data-ttu-id="92584-103">大部分的企業，在某個時間點，購買多台印表機的相同模型。</span><span class="sxs-lookup"><span data-stu-id="92584-103">Most businesses will, at some point, buy multiple printers of the same model.</span></span> <span data-ttu-id="92584-104">一般而言，這些所有在安裝有幾乎相同的組態設定。</span><span class="sxs-lookup"><span data-stu-id="92584-104">Typically, these are all installed with virtually identical configuration settings.</span></span> <span data-ttu-id="92584-105">安裝每一部印表機可能會很費時而且容易產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="92584-105">Installing each printer can be time-consuming and error prone.</span></span> <span data-ttu-id="92584-106"><xref:System.Printing.IndexedProperties?displayProperty=nameWithType>命名空間和<xref:System.Printing.PrintServer.InstallPrintQueue%2A>都會以 Microsoft.NET Framework 公開的類別會讓您能夠立即安裝任何數目的其他列印佇列，就會遭到複製，從現有的列印佇列。</span><span class="sxs-lookup"><span data-stu-id="92584-106">The <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace and the <xref:System.Printing.PrintServer.InstallPrintQueue%2A> class that are exposed with Microsoft .NET Framework makes it possible to instantly install any number of additional print queues that are cloned from an existing print queue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92584-107">範例</span><span class="sxs-lookup"><span data-stu-id="92584-107">Example</span></span>  
 <span data-ttu-id="92584-108">在下列範例中，第二個列印佇列會複製從現有的列印佇列。</span><span class="sxs-lookup"><span data-stu-id="92584-108">In the example below, a second print queue is cloned from an existing print queue.</span></span> <span data-ttu-id="92584-109">第二個後者只能在其名稱、 位置、 連接埠，以及共用的狀態。</span><span class="sxs-lookup"><span data-stu-id="92584-109">The second differs from the first only in its name, location, port, and shared status.</span></span> <span data-ttu-id="92584-110">執行此作業的主要步驟如下所示。</span><span class="sxs-lookup"><span data-stu-id="92584-110">The major steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="92584-111">建立<xref:System.Printing.PrintQueue>現有印表機即將複製的物件。</span><span class="sxs-lookup"><span data-stu-id="92584-111">Create a <xref:System.Printing.PrintQueue> object for the existing printer that is going to be cloned.</span></span>  
  
2.  <span data-ttu-id="92584-112">建立<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>從<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>的<xref:System.Printing.PrintQueue>。</span><span class="sxs-lookup"><span data-stu-id="92584-112">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> of the <xref:System.Printing.PrintQueue>.</span></span> <span data-ttu-id="92584-113"><xref:System.Collections.DictionaryEntry.Value%2A>此字典中的每個項目的屬性是物件的其中一個衍生自類型<xref:System.Printing.IndexedProperties.PrintProperty>。</span><span class="sxs-lookup"><span data-stu-id="92584-113">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span> <span data-ttu-id="92584-114">有兩種方式，在此字典中設定的項目值。</span><span class="sxs-lookup"><span data-stu-id="92584-114">There are two ways to set the value of an entry in this dictionary.</span></span>  
  
    -   <span data-ttu-id="92584-115">使用此字典**移除**和<xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A>方法來移除該項目，然後重新加入想要的值。</span><span class="sxs-lookup"><span data-stu-id="92584-115">Use the dictionary's **Remove** and <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> methods to remove the entry and then re-add it with the desired value.</span></span>  
  
    -   <span data-ttu-id="92584-116">使用此字典<xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="92584-116">Use the dictionary's <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> method.</span></span>  
  
     <span data-ttu-id="92584-117">下列範例會示範這兩種方式。</span><span class="sxs-lookup"><span data-stu-id="92584-117">The example below illustrates both ways.</span></span>  
  
3.  <span data-ttu-id="92584-118">建立<xref:System.Printing.IndexedProperties.PrintBooleanProperty>物件，並設定其<xref:System.Printing.IndexedProperties.PrintProperty.Name%2A>"IsShared 」 至及其<xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A>至`true`。</span><span class="sxs-lookup"><span data-stu-id="92584-118">Create a <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "IsShared" and its <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="92584-119">使用<xref:System.Printing.IndexedProperties.PrintBooleanProperty>物件的值<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>的"IsShared"項目。</span><span class="sxs-lookup"><span data-stu-id="92584-119">Use the <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" entry.</span></span>  
  
5.  <span data-ttu-id="92584-120">建立<xref:System.Printing.IndexedProperties.PrintStringProperty>物件，並設定其<xref:System.Printing.IndexedProperties.PrintProperty.Name%2A>至 「 共用 」 的名稱和其<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>適當<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="92584-120">Create a <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "ShareName" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
6.  <span data-ttu-id="92584-121">使用<xref:System.Printing.IndexedProperties.PrintStringProperty>物件的值<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>的 」 共用名稱"項目。</span><span class="sxs-lookup"><span data-stu-id="92584-121">Use the <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" entry.</span></span>  
  
7.  <span data-ttu-id="92584-122">建立另一個<xref:System.Printing.IndexedProperties.PrintStringProperty>物件，並設定其<xref:System.Printing.IndexedProperties.PrintProperty.Name%2A>至 「 位置 」 和其<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>適當<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="92584-122">Create another <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "Location" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
8.  <span data-ttu-id="92584-123">使用第二個<xref:System.Printing.IndexedProperties.PrintStringProperty>物件的值<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>的 「 位置 」 項目。</span><span class="sxs-lookup"><span data-stu-id="92584-123">Use the second <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Location" entry.</span></span>  
  
9. <span data-ttu-id="92584-124">建立陣列<xref:System.String>s。</span><span class="sxs-lookup"><span data-stu-id="92584-124">Create an array of <xref:System.String>s.</span></span> <span data-ttu-id="92584-125">每個項目是在伺服器上的連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="92584-125">Each item is the name of a port on the server.</span></span>  
  
10. <span data-ttu-id="92584-126">使用<xref:System.Printing.PrintServer.InstallPrintQueue%2A>安裝新印表機的新值。</span><span class="sxs-lookup"><span data-stu-id="92584-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> to install the new printer with the new values.</span></span>  
  
 <span data-ttu-id="92584-127">以下是範例。</span><span class="sxs-lookup"><span data-stu-id="92584-127">An example is below.</span></span>  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a><span data-ttu-id="92584-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92584-128">See Also</span></span>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="92584-129">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="92584-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="92584-130">列印概觀</span><span class="sxs-lookup"><span data-stu-id="92584-130">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
