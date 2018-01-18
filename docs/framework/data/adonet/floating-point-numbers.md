---
title: "浮點數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9a090d02b9c2ce63bd265996d237aab5c30f61bf
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="floating-point-numbers"></a><span data-ttu-id="8c65b-102">浮點數</span><span class="sxs-lookup"><span data-stu-id="8c65b-102">Floating-Point Numbers</span></span>
<span data-ttu-id="8c65b-103">本主題說明開發人員在 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中使用浮點數值 (Floating-Point Number) 時經常遇到的一些問題。</span><span class="sxs-lookup"><span data-stu-id="8c65b-103">This topic describes some of the issues that developers frequently encounter when they work with floating-point numbers in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span> <span data-ttu-id="8c65b-104">這些問題是由電腦儲存浮點數值的方式而導致，而不是特定提供者 (例如 <xref:System.Data.SqlClient> 或 <xref:System.Data.OracleClient>) 所特有。</span><span class="sxs-lookup"><span data-stu-id="8c65b-104">These issues are caused by the way that computers store floating-point numbers, and are not specific to a particular provider such as <xref:System.Data.SqlClient> or <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="8c65b-105">一般而言，浮點數值並不具有完全符合的二進位表示，</span><span class="sxs-lookup"><span data-stu-id="8c65b-105">Floating-point numbers generally do not have an exact binary representation.</span></span> <span data-ttu-id="8c65b-106">而是由電腦儲存該數值的近似值。</span><span class="sxs-lookup"><span data-stu-id="8c65b-106">Instead, the computer stores an approximation of the number.</span></span> <span data-ttu-id="8c65b-107">在不同的時間可能會使用不同的位元來表示該數值。</span><span class="sxs-lookup"><span data-stu-id="8c65b-107">At different times, different numbers of binary digits may be used to represent the number.</span></span> <span data-ttu-id="8c65b-108">當浮點數值從一種表示法轉換為另一種時，該數值的最小顯著性數字可能會稍微變更。</span><span class="sxs-lookup"><span data-stu-id="8c65b-108">When a floating point number is converted from one representation to another representation, the least significant digits of that number may vary slightly.</span></span> <span data-ttu-id="8c65b-109">轉換通常發生在當數值從一種型別轉型為另一種型別時。</span><span class="sxs-lookup"><span data-stu-id="8c65b-109">Conversion typically occurs when the number is cast from one type to another type.</span></span> <span data-ttu-id="8c65b-110">不論轉換是發生在資料庫內、在表示資料庫值的型別之間或是在型別之間，都會造成最小顯著性數字的變更。</span><span class="sxs-lookup"><span data-stu-id="8c65b-110">The variation occurs whether the conversion occurs within a database, between types that represent database values, or between types.</span></span> <span data-ttu-id="8c65b-111">因為有這些變更，所以邏輯上應該相同的數值，可能因為最小顯著性數字變更而導致它們擁有不同的值。</span><span class="sxs-lookup"><span data-stu-id="8c65b-111">Because of these changes, numbers that would logically be equal may have changes in their least-significant digits that cause them to have different values.</span></span> <span data-ttu-id="8c65b-112">數值的精確度位數可能會比預期的多或少。</span><span class="sxs-lookup"><span data-stu-id="8c65b-112">The number of digits of precision in the number may be larger or smaller than expected.</span></span> <span data-ttu-id="8c65b-113">如果將數值的格式設為字串，則該數值可能不會顯示預期的值。</span><span class="sxs-lookup"><span data-stu-id="8c65b-113">When formatted as a string, the number may not show the expected value.</span></span>  
  
 <span data-ttu-id="8c65b-114">若要盡可能減少這些效果，您應該就可用的項目中，選用最接近的數值型別相符項目。</span><span class="sxs-lookup"><span data-stu-id="8c65b-114">To minimize these effects, you should use the closest match between numeric types that is available to you.</span></span> <span data-ttu-id="8c65b-115">例如，如果使用的是 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]，而且將實際型別的 Transact-SQL 值轉換成浮點型別的值，則完全符合的數值可能會變更。</span><span class="sxs-lookup"><span data-stu-id="8c65b-115">For example, if you are working with [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], the exact numeric value may change if you convert a Transact-SQL value of real type to a value of float type.</span></span> <span data-ttu-id="8c65b-116">在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中將 <xref:System.Single> 轉換成 <xref:System.Double> 可能也會造成未預期的結果。</span><span class="sxs-lookup"><span data-stu-id="8c65b-116">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], converting a <xref:System.Single> to a <xref:System.Double> may also produce unexpected results.</span></span> <span data-ttu-id="8c65b-117">在上述兩種情況中，將應用程式中的所有值設定為使用相同的數字型別 (Numeric Type) 是不錯的策略。</span><span class="sxs-lookup"><span data-stu-id="8c65b-117">In both of these cases, a good strategy is to make all the values in the application use the same numeric type.</span></span> <span data-ttu-id="8c65b-118">您也可以使用固定有效位數十進位型別，或者將浮點數值轉型為固定有效位數十進位型別，再加以使用。</span><span class="sxs-lookup"><span data-stu-id="8c65b-118">You can also use a fixed-precision decimal type, or cast floating-point numbers to a fixed-precision decimal type before you work with them.</span></span>  
  
 <span data-ttu-id="8c65b-119">若要解決等號比較的問題，請考慮撰寫應用程式的程式碼，使最小顯著性數字中的變更可以忽略。</span><span class="sxs-lookup"><span data-stu-id="8c65b-119">To work around problems with equality comparison, consider coding your application so that variations in the least significant digits are ignored.</span></span> <span data-ttu-id="8c65b-120">例如，與其比較兩個數字是否相等，請從一個數字中減去另一個數字。</span><span class="sxs-lookup"><span data-stu-id="8c65b-120">For example, instead of comparing to see whether two numbers are equal, subtract one number from the other number.</span></span> <span data-ttu-id="8c65b-121">如果差異是在可接受的捨入範圍內，則應用程式可以將這兩個數字視為相同。</span><span class="sxs-lookup"><span data-stu-id="8c65b-121">If the difference is within an acceptable margin of rounding, your application can treat the numbers as if they are the same.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c65b-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="8c65b-122">See Also</span></span>  
 [<span data-ttu-id="8c65b-123">浮點數會失去精確度的原因</span><span class="sxs-lookup"><span data-stu-id="8c65b-123">Why Floating-Point Numbers May Lose Precision</span></span>](http://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)  
 [<span data-ttu-id="8c65b-124">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="8c65b-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
