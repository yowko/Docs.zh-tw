---
title: HOW TO：測試 Point4D 結構是否相等和不相等
ms.date: 03/30/2017
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
ms.openlocfilehash: d72aef8a1328742f0b04c2ad009126e21390398a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367202"
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a><span data-ttu-id="5e9ee-102">HOW TO：測試 Point4D 結構是否相等和不相等</span><span class="sxs-lookup"><span data-stu-id="5e9ee-102">How to: Test Point4D structures for equality and inequality</span></span>
<span data-ttu-id="5e9ee-103">此範例示範如何測試<xref:System.Windows.Media.Media3D.Point4D>結構是否相等和不等比較。</span><span class="sxs-lookup"><span data-stu-id="5e9ee-103">This example shows how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality.</span></span>  
  
 <span data-ttu-id="5e9ee-104">下列程式碼說明如何測試<xref:System.Windows.Media.Media3D.Point4D>結構是否相等和不等比較使用<xref:System.Windows.Media.Media3D.Point4D>等號比較方法。</span><span class="sxs-lookup"><span data-stu-id="5e9ee-104">The following code illustrates how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality using the <xref:System.Windows.Media.Media3D.Point4D> equality methods.</span></span>  <span data-ttu-id="5e9ee-105"><xref:System.Windows.Media.Media3D.Point4D>結構的測試方式，使用多載等號比較是否相等 (`==`) 運算子，然後使用多載不等比較的不等比較 (`!=`) 運算子，最後<xref:System.Windows.Media.Media3D.Point3D>結構和<xref:System.Windows.Media.Media3D.Point4D>結構會檢查是否有使用靜態等號比較<xref:System.Windows.Media.Media3D.Point4D.Equals%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="5e9ee-105">The <xref:System.Windows.Media.Media3D.Point4D> structures are tested for equality using the overloaded equality (`==`) operator, then for inequality using the overloaded inequality (`!=`) operator, and finally a <xref:System.Windows.Media.Media3D.Point3D> structure and a <xref:System.Windows.Media.Media3D.Point4D> structure are checked for equality using the static <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e9ee-106">範例</span><span class="sxs-lookup"><span data-stu-id="5e9ee-106">Example</span></span>  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a><span data-ttu-id="5e9ee-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e9ee-107">See also</span></span>
- <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
