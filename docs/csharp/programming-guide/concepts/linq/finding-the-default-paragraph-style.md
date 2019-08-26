---
title: 尋找預設段落樣式 (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 702d3906f51b996f59dcd15067702b6de07c60a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594371"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="d5ec3-102">尋找預設段落樣式 (C#)</span><span class="sxs-lookup"><span data-stu-id="d5ec3-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="d5ec3-103">＜管理 WordprocessingML 文件中的資訊＞教學課程中的第一個工作是，尋找文件中的預設段落樣式。</span><span class="sxs-lookup"><span data-stu-id="d5ec3-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5ec3-104">範例</span><span class="sxs-lookup"><span data-stu-id="d5ec3-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d5ec3-105">說明</span><span class="sxs-lookup"><span data-stu-id="d5ec3-105">Description</span></span>  
 <span data-ttu-id="d5ec3-106">下列範例會開啟 Office Open XML WordprocessingML 文件、尋找文件和封裝的樣式部分，然後執行尋找預設樣式名稱的查詢。</span><span class="sxs-lookup"><span data-stu-id="d5ec3-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="d5ec3-107">如需 Office Open XML 文件套件及其組成部分的詳細資訊，請參閱 [Office Open XML WordprocessingML 文件的詳細資料 (C#)](./wordprocessingml-document-with-styles.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ec3-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="d5ec3-108">查詢會尋找名稱為 `w:style` 的節點，其中擁有名稱為 `w:type` 且值為 "paragraph" 的屬性，同時也擁有名稱為 `w:default` 且值為 "1" 的屬性。</span><span class="sxs-lookup"><span data-stu-id="d5ec3-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="d5ec3-109">由於這些屬性只有一個 XML 節點，查詢會使用 <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> 運算子，將集合轉換為單一子句。</span><span class="sxs-lookup"><span data-stu-id="d5ec3-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="d5ec3-110">接著，它會取得名稱為 `w:styleId` 之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d5ec3-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="d5ec3-111">這個範例會使用 WindowsBase 組件的類別。</span><span class="sxs-lookup"><span data-stu-id="d5ec3-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="d5ec3-112">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="d5ec3-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d5ec3-113">程式碼</span><span class="sxs-lookup"><span data-stu-id="d5ec3-113">Code</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
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
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a><span data-ttu-id="d5ec3-114">註解</span><span class="sxs-lookup"><span data-stu-id="d5ec3-114">Comments</span></span>  
 <span data-ttu-id="d5ec3-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d5ec3-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="d5ec3-116">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d5ec3-116">Next Steps</span></span>  
 <span data-ttu-id="d5ec3-117">在下一個範例中，您將建立可在文件中尋找所有段落及其樣式的類似查詢：</span><span class="sxs-lookup"><span data-stu-id="d5ec3-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="d5ec3-118">擷取段落及其樣式 (C#)</span><span class="sxs-lookup"><span data-stu-id="d5ec3-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  
  