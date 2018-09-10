---
title: 輸出 Office Open XML 文件部分內容的範例 (C#)
ms.date: 07/20/2015
ms.assetid: 6cd37055-89b4-42e8-bf27-5a29717e35f3
ms.openlocfilehash: 5dd8e4238ff4015130160b5297f807d79013ce7b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505667"
---
# <a name="example-that-outputs-office-open-xml-document-parts-c"></a><span data-ttu-id="a0711-102">輸出 Office Open XML 文件部分內容的範例 (C#)</span><span class="sxs-lookup"><span data-stu-id="a0711-102">Example that Outputs Office Open XML Document Parts (C#)</span></span>
<span data-ttu-id="a0711-103">本主題顯示如何開啟 Office Open XML 文件並存取其中的一部分。</span><span class="sxs-lookup"><span data-stu-id="a0711-103">This topic shows how to open an Office Open XML document and access parts within it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0711-104">範例</span><span class="sxs-lookup"><span data-stu-id="a0711-104">Example</span></span>  
 <span data-ttu-id="a0711-105">下列範例會開啟 Office Open XML 文件，並列印主控台的文件部分與樣式部分。</span><span class="sxs-lookup"><span data-stu-id="a0711-105">The following example opens an Office Open XML document, and prints the document part and the style part to the console.</span></span>  
  
 <span data-ttu-id="a0711-106">這個範例會使用 WindowsBase 組件的類別。</span><span class="sxs-lookup"><span data-stu-id="a0711-106">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="a0711-107">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="a0711-107">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship =  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
          docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        XDocument xdoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        Console.WriteLine("TargetUri:{0}", docPackageRelationship.TargetUri);  
        Console.WriteLine("==================================================================");  
        Console.WriteLine(xdoc.Root);  
        Console.WriteLine();  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            XDocument styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
  
            Console.WriteLine("TargetUri:{0}", styleRelation.TargetUri);  
            Console.WriteLine("==================================================================");  
            Console.WriteLine(styleDoc.Root);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0711-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0711-108">See Also</span></span>

- [<span data-ttu-id="a0711-109">Office Open XML WordprocessingML 文件的詳細資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="a0711-109">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)
