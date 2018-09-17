---
title: XSLT 擴充物件
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40a530190ee4b19d72399ab877cf26bad1090b9f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45649324"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="f2c8f-102">XSLT 擴充物件</span><span class="sxs-lookup"><span data-stu-id="f2c8f-102">XSLT Extension Objects</span></span>
<span data-ttu-id="f2c8f-103">擴充物件可用來擴充樣式表的功能。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="f2c8f-104"><xref:System.Xml.Xsl.XsltArgumentList> 類別會維護擴充物件。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="f2c8f-105">以下是使用擴充物件而不使用內嵌指令碼的優點：</span><span class="sxs-lookup"><span data-stu-id="f2c8f-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="f2c8f-106">提供較佳的類別封裝和重複使用。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="f2c8f-107">允許樣式表更簡潔且更易於維護。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="f2c8f-108">使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法，將 XSLT 擴充物件加入至 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 物件。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="f2c8f-109">限定名稱和命名空間 URI 於當時與擴充物件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2c8f-110">呼叫 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法，需要 FullTrust 使用權限集合。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="f2c8f-111">如需詳細資訊，請參閱[程式碼存取安全性](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)和 [NIB：具名使用權限集合](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3)。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-111">For more information, see [Code Access Security](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="f2c8f-112">從擴充物件傳回的資料型別，是 `number`、`string`、`Boolean` 及 `node set` 這四種基本 XPath 資料型別之一。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="f2c8f-113">`params` 類別目前不支援任何允許傳遞未指定的參數數目，並以 <xref:System.Xml.Xsl.XslCompiledTransform> 關鍵字定義的方法。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f2c8f-114">使用以 `params` 關鍵字定義之任何方法的 XSLT 樣式表將無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="f2c8f-115">如需詳細資訊，請查看 [params](~/docs/csharp/language-reference/keywords/params.md)。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="f2c8f-116">使用 XSLT 擴充物件</span><span class="sxs-lookup"><span data-stu-id="f2c8f-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="f2c8f-117">使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法，建立 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 物件並加入擴充物件。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="f2c8f-118">從樣式表呼叫擴充物件。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="f2c8f-119">將 <xref:System.Xml.Xsl.XsltArgumentList> 物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f2c8f-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2c8f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2c8f-120">See also</span></span>

- [<span data-ttu-id="f2c8f-121">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="f2c8f-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [<span data-ttu-id="f2c8f-122">XSLT 安全性考量</span><span class="sxs-lookup"><span data-stu-id="f2c8f-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
