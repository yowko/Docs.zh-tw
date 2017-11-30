---
title: "HOW TO：使用組件執行 XSLT 轉換"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f236296d604bc465973d17d63883e7b212b7f02d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a><span data-ttu-id="e800e-102">HOW TO：使用組件執行 XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="e800e-102">How to: Perform an XSLT Transformation by Using an Assembly</span></span>
<span data-ttu-id="e800e-103">XSLT 編譯器 (xsltc.exe) 會編譯 XSLT 樣式表並產生組件。</span><span class="sxs-lookup"><span data-stu-id="e800e-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="e800e-104">然後此組件可以直接傳遞到 <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> 方法中。</span><span class="sxs-lookup"><span data-stu-id="e800e-104">The assembly can be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a><span data-ttu-id="e800e-105">將 XML 和 XSLT 檔案複製到本機電腦</span><span class="sxs-lookup"><span data-stu-id="e800e-105">To copy the XML and XSLT files to your local computer</span></span>  
  
-   <span data-ttu-id="e800e-106">將 XSLT 檔案複製到本機電腦，並將它命名為 Transform.xsl。</span><span class="sxs-lookup"><span data-stu-id="e800e-106">Copy the XSLT file to your local computer and name it Transform.xsl.</span></span>  
  
    ```xml  
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
      xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
      xmlns:user="urn:my-scripts">  
      <msxsl:script language="C#" implements-prefix="user">  
        <![CDATA[  
      public string discount(string price){  
        char[] trimChars = { '$' };  
        //trim leading $, convert price to type double  
        double discount_value = Convert.ToDouble(price.TrimStart(trimChars));  
        //apply 10% discount and round appropriately  
        discount_value = .9*discount_value;  
        //convert value to decimal and format as currency  
        string discount_price = discount_value.ToString("C");  
        return discount_price;  
      }  
      ]]>  
      </msxsl:script>  
      <xsl:template match="catalog">  
        <html>  
          <head></head>  
          <body>  
            <table border="1">  
              <tr>  
                <th align="left">Title</th>  
                <th align="left">Author</th>  
                <th align="left">Genre</th>  
                <th align="left">Publish Date</th>  
                <th align="left">Price</th>  
              </tr>  
              <xsl:for-each select="book">  
                <tr>  
                  <td>  
                    <xsl:value-of select="title"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="author"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="genre"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="publish_date"/>  
                  </td>  
                  <xsl:choose>  
                    <xsl:when test="genre = 'Fantasy'">  
                      <td>  
                        <xsl:value-of select="user:discount(price)"/>  
                      </td>  
                    </xsl:when>  
                    <xsl:otherwise>  
                      <td>  
                        <xsl:value-of select="price"/>  
                      </td>  
                    </xsl:otherwise>  
                  </xsl:choose>  
                </tr>  
              </xsl:for-each>  
            </table>  
          </body>  
        </html>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
-   <span data-ttu-id="e800e-107">將 XML 檔案複製到本機電腦，並將它命名為 `books.xml`。</span><span class="sxs-lookup"><span data-stu-id="e800e-107">Copy the XML file to your local computer and name it `books.xml`.</span></span>  
  
    ```xml  
    <?xml version="1.0"?>  
    <catalog>  
       <book id="bk101">  
          <author>Gambardella, Matthew</author>  
          <title>XML Developer's Guide</title>  
          <genre>Computer</genre>  
          <price>$44.95</price>  
          <publish_date>2000-10-01</publish_date>  
       </book>  
       <book id="bk102">  
          <author>Ralls, Kim</author>  
          <title>Midnight Rain</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-12-16</publish_date>  
       </book>  
       <book id="bk103">  
          <author>Corets, Eva</author>  
          <title>Maeve Ascendant</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-11-17</publish_date>  
       </book>  
       <book id="bk106">  
          <author>Randall, Cynthia</author>  
          <title>Lover Birds</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-09-02</publish_date>  
       </book>  
       <book id="bk107">  
          <author>Thurman, Paula</author>  
          <title>Splish Splash</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-11-02</publish_date>  
       </book>  
    </catalog>  
    ```  
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a><span data-ttu-id="e800e-108">在啟用指令碼的情況下編譯樣式表。</span><span class="sxs-lookup"><span data-stu-id="e800e-108">To compile the style sheet with the script enabled.</span></span>  
  
1.  <span data-ttu-id="e800e-109">從命令列執行下列命令會建立兩個名為 `Transform.dll` 和 `Transform_Script1.dll` 的組件 (這是預設行為。</span><span class="sxs-lookup"><span data-stu-id="e800e-109">Executing the following command from the command line creates two assemblies named `Transform.dll` and `Transform_Script1.dll` (This is the default behavior.</span></span> <span data-ttu-id="e800e-110">除非另外指定，否則類別和組件的名稱會預設為主要樣式表的名稱)：</span><span class="sxs-lookup"><span data-stu-id="e800e-110">Unless otherwise specified, the name of the class and the assembly defaults to the name of the main style sheet):</span></span>  
  
    ```  
    xsltc /settings:script+ Transform.xsl  
    ```  
  
 <span data-ttu-id="e800e-111">下列命令會明確將類別名稱設定為 Transform：</span><span class="sxs-lookup"><span data-stu-id="e800e-111">The following command explicitly sets the class name to Transform:</span></span>  
  
```  
xsltc /settings:script+ /class:Transform Transform.xsl  
```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a><span data-ttu-id="e800e-112">當您在編譯程式碼時，將編譯的組件當做參考併入</span><span class="sxs-lookup"><span data-stu-id="e800e-112">To include the compiled assembly as a reference when you compile your code.</span></span>  
  
1.  <span data-ttu-id="e800e-113">您可以在 Visual Studio 中包含組件，其方式是在 [方案總管] 內或是從命令列加入參考。</span><span class="sxs-lookup"><span data-stu-id="e800e-113">You can include an assembly in Visual Studio by adding a reference in the Solution Explorer, or from the command line.</span></span>  
  
2.  <span data-ttu-id="e800e-114">如果是使用 C# 的命令列，請使用以下程式碼：</span><span class="sxs-lookup"><span data-stu-id="e800e-114">For the command line with C#, use the following:</span></span>  
  
    ```  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3.  <span data-ttu-id="e800e-115">如果是使用 Visual Basic 的命令列，請使用以下程式碼：</span><span class="sxs-lookup"><span data-stu-id="e800e-115">For the command line with Visual Basic, use the following</span></span>  
  
    ```  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a><span data-ttu-id="e800e-116">在程式碼中使用編譯的組件</span><span class="sxs-lookup"><span data-stu-id="e800e-116">To use the compiled assembly in your code.</span></span>  
  
1.  <span data-ttu-id="e800e-117">下列範例將示範如何使用編譯的樣式表執行 XSLT 轉換。</span><span class="sxs-lookup"><span data-stu-id="e800e-117">The following example shows how to execute the XSLT transformation by using the compiled style sheet.</span></span>  
  
 [!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
 [!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
 <span data-ttu-id="e800e-118">若要動態連結至已編譯的組件，請將</span><span class="sxs-lookup"><span data-stu-id="e800e-118">To dynamically link to the compiled assembly, replace</span></span>  
  
```  
xslt.Load(typeof(Transform))  
```  
  
 <span data-ttu-id="e800e-119">取代為</span><span class="sxs-lookup"><span data-stu-id="e800e-119">with</span></span>  
  
```  
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"))  
```  
  
 <span data-ttu-id="e800e-120">。</span><span class="sxs-lookup"><span data-stu-id="e800e-120">in the example above.</span></span> <span data-ttu-id="e800e-121">如需 Assembly.Load 方法的詳細資訊，請參閱 <xref:System.Reflection.Assembly.Load%2A></span><span class="sxs-lookup"><span data-stu-id="e800e-121">For more information on the Assembly.Load method, see <xref:System.Reflection.Assembly.Load%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e800e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e800e-122">See Also</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="e800e-123">XSLT 編譯器 (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="e800e-123">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 [<span data-ttu-id="e800e-124">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="e800e-124">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="e800e-125">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="e800e-125">Command-line Building With csc.exe</span></span>](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
