---
title: "OLE DB 結構描述集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 33e794559abd7f619f7431683f06e59705b57d41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="8c7ba-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="8c7ba-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="8c7ba-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="8c7ba-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="8c7ba-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="8c7ba-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="8c7ba-105">Microsoft SQL Server OLE DB 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="8c7ba-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="8c7ba-106">資料表</span><span class="sxs-lookup"><span data-stu-id="8c7ba-106">Tables</span></span>  
  
-   <span data-ttu-id="8c7ba-107">資料行</span><span class="sxs-lookup"><span data-stu-id="8c7ba-107">Columns</span></span>  
  
-   <span data-ttu-id="8c7ba-108">程序</span><span class="sxs-lookup"><span data-stu-id="8c7ba-108">Procedures</span></span>  
  
-   <span data-ttu-id="8c7ba-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8c7ba-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="8c7ba-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="8c7ba-110">Catalog</span></span>  
  
-   <span data-ttu-id="8c7ba-111">Indexes</span><span class="sxs-lookup"><span data-stu-id="8c7ba-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="8c7ba-112">資料表</span><span class="sxs-lookup"><span data-stu-id="8c7ba-112">Tables</span></span>  
  
|<span data-ttu-id="8c7ba-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-113">ColumnName</span></span>|<span data-ttu-id="8c7ba-114">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-115">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-116">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-116">String</span></span>|  
|<span data-ttu-id="8c7ba-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-118">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-118">String</span></span>|  
|<span data-ttu-id="8c7ba-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-119">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-120">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-120">String</span></span>|  
|<span data-ttu-id="8c7ba-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-121">TABLE_TYPE</span></span>|<span data-ttu-id="8c7ba-122">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-122">String</span></span>|  
|<span data-ttu-id="8c7ba-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-123">TABLE_GUID</span></span>|<span data-ttu-id="8c7ba-124">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-124">Guid</span></span>|  
|<span data-ttu-id="8c7ba-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-125">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-126">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-126">String</span></span>|  
|<span data-ttu-id="8c7ba-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-127">TABLE_PROPID</span></span>|<span data-ttu-id="8c7ba-128">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-128">Int64</span></span>|  
|<span data-ttu-id="8c7ba-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-129">DATE_CREATED</span></span>|<span data-ttu-id="8c7ba-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-130">DateTime</span></span>|  
|<span data-ttu-id="8c7ba-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-131">DATE_MODIFIED</span></span>|<span data-ttu-id="8c7ba-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8c7ba-133">資料行</span><span class="sxs-lookup"><span data-stu-id="8c7ba-133">Columns</span></span>  
  
|<span data-ttu-id="8c7ba-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-134">ColumnName</span></span>|<span data-ttu-id="8c7ba-135">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-136">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-137">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-137">String</span></span>|  
|<span data-ttu-id="8c7ba-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-139">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-139">String</span></span>|  
|<span data-ttu-id="8c7ba-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-140">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-141">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-141">String</span></span>|  
|<span data-ttu-id="8c7ba-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-142">COLUMN_NAME</span></span>|<span data-ttu-id="8c7ba-143">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-143">String</span></span>|  
|<span data-ttu-id="8c7ba-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-144">COLUMN_GUID</span></span>|<span data-ttu-id="8c7ba-145">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-145">Guid</span></span>|  
|<span data-ttu-id="8c7ba-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-146">COLUMN_PROPID</span></span>|<span data-ttu-id="8c7ba-147">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-147">Int64</span></span>|  
|<span data-ttu-id="8c7ba-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="8c7ba-149">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-149">Int64</span></span>|  
|<span data-ttu-id="8c7ba-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8c7ba-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="8c7ba-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-151">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8c7ba-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="8c7ba-153">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-153">String</span></span>|  
|<span data-ttu-id="8c7ba-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8c7ba-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="8c7ba-155">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-155">Int64</span></span>|  
|<span data-ttu-id="8c7ba-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-156">IS_NULLABLE</span></span>|<span data-ttu-id="8c7ba-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-157">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-158">DATA_TYPE</span></span>|<span data-ttu-id="8c7ba-159">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-159">Int32</span></span>|  
|<span data-ttu-id="8c7ba-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-160">TYPE_GUID</span></span>|<span data-ttu-id="8c7ba-161">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-161">Guid</span></span>|  
|<span data-ttu-id="8c7ba-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8c7ba-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8c7ba-163">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-163">Int64</span></span>|  
|<span data-ttu-id="8c7ba-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8c7ba-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8c7ba-165">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-165">Int64</span></span>|  
|<span data-ttu-id="8c7ba-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8c7ba-167">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-167">Int32</span></span>|  
|<span data-ttu-id="8c7ba-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="8c7ba-169">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-169">Int16</span></span>|  
|<span data-ttu-id="8c7ba-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="8c7ba-171">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-171">Int64</span></span>|  
|<span data-ttu-id="8c7ba-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="8c7ba-173">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-173">String</span></span>|  
|<span data-ttu-id="8c7ba-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="8c7ba-175">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-175">String</span></span>|  
|<span data-ttu-id="8c7ba-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="8c7ba-177">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-177">String</span></span>|  
|<span data-ttu-id="8c7ba-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="8c7ba-179">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-179">String</span></span>|  
|<span data-ttu-id="8c7ba-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="8c7ba-181">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-181">String</span></span>|  
|<span data-ttu-id="8c7ba-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-182">COLLATION_NAME</span></span>|<span data-ttu-id="8c7ba-183">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-183">String</span></span>|  
|<span data-ttu-id="8c7ba-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="8c7ba-185">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-185">String</span></span>|  
|<span data-ttu-id="8c7ba-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="8c7ba-187">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-187">String</span></span>|  
|<span data-ttu-id="8c7ba-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-188">DOMAIN_NAME</span></span>|<span data-ttu-id="8c7ba-189">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-189">String</span></span>|  
|<span data-ttu-id="8c7ba-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-190">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-191">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-191">String</span></span>|  
|<span data-ttu-id="8c7ba-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-192">COLUMN_LCID</span></span>|<span data-ttu-id="8c7ba-193">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-193">Int32</span></span>|  
|<span data-ttu-id="8c7ba-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="8c7ba-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="8c7ba-195">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-195">Int32</span></span>|  
|<span data-ttu-id="8c7ba-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-196">COLUMN_SORTID</span></span>|<span data-ttu-id="8c7ba-197">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-197">Int32</span></span>|  
|<span data-ttu-id="8c7ba-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="8c7ba-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="8c7ba-199">Byte[]</span></span>|  
|<span data-ttu-id="8c7ba-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-200">IS_COMPUTED</span></span>|<span data-ttu-id="8c7ba-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8c7ba-202">程序</span><span class="sxs-lookup"><span data-stu-id="8c7ba-202">Procedures</span></span>  
  
|<span data-ttu-id="8c7ba-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-203">ColumnName</span></span>|<span data-ttu-id="8c7ba-204">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8c7ba-206">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-206">String</span></span>|  
|<span data-ttu-id="8c7ba-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-208">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-208">String</span></span>|  
|<span data-ttu-id="8c7ba-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="8c7ba-210">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-210">String</span></span>|  
|<span data-ttu-id="8c7ba-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8c7ba-212">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-212">Int16</span></span>|  
|<span data-ttu-id="8c7ba-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="8c7ba-214">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-214">String</span></span>|  
|<span data-ttu-id="8c7ba-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-215">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-216">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-216">String</span></span>|  
|<span data-ttu-id="8c7ba-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-217">DATE_CREATED</span></span>|<span data-ttu-id="8c7ba-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-218">DateTime</span></span>|  
|<span data-ttu-id="8c7ba-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-219">DATE_MODIFIED</span></span>|<span data-ttu-id="8c7ba-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="8c7ba-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8c7ba-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="8c7ba-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-222">ColumnName</span></span>|<span data-ttu-id="8c7ba-223">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8c7ba-225">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-225">String</span></span>|  
|<span data-ttu-id="8c7ba-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-227">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-227">String</span></span>|  
|<span data-ttu-id="8c7ba-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="8c7ba-229">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-229">String</span></span>|  
|<span data-ttu-id="8c7ba-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-230">PARAMETER_NAME</span></span>|<span data-ttu-id="8c7ba-231">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-231">String</span></span>|  
|<span data-ttu-id="8c7ba-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="8c7ba-233">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-233">Int32</span></span>|  
|<span data-ttu-id="8c7ba-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="8c7ba-235">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-235">Int32</span></span>|  
|<span data-ttu-id="8c7ba-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8c7ba-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="8c7ba-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-237">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8c7ba-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="8c7ba-239">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-239">String</span></span>|  
|<span data-ttu-id="8c7ba-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-240">IS_NULLABLE</span></span>|<span data-ttu-id="8c7ba-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-241">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-242">DATA_TYPE</span></span>|<span data-ttu-id="8c7ba-243">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-243">Int32</span></span>|  
|<span data-ttu-id="8c7ba-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8c7ba-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8c7ba-245">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-245">Int64</span></span>|  
|<span data-ttu-id="8c7ba-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8c7ba-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8c7ba-247">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-247">Int64</span></span>|  
|<span data-ttu-id="8c7ba-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8c7ba-249">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-249">Int32</span></span>|  
|<span data-ttu-id="8c7ba-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="8c7ba-251">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-251">Int16</span></span>|  
|<span data-ttu-id="8c7ba-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-252">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-253">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-253">String</span></span>|  
|<span data-ttu-id="8c7ba-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-254">TYPE_NAME</span></span>|<span data-ttu-id="8c7ba-255">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-255">String</span></span>|  
|<span data-ttu-id="8c7ba-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="8c7ba-257">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="8c7ba-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="8c7ba-258">Catalog</span></span>  
  
|<span data-ttu-id="8c7ba-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-259">ColumnName</span></span>|<span data-ttu-id="8c7ba-260">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-261">CATALOG_NAME</span></span>|<span data-ttu-id="8c7ba-262">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-262">String</span></span>|  
|<span data-ttu-id="8c7ba-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-263">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-264">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8c7ba-265">Indexes</span><span class="sxs-lookup"><span data-stu-id="8c7ba-265">Indexes</span></span>  
  
|<span data-ttu-id="8c7ba-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-266">ColumnName</span></span>|<span data-ttu-id="8c7ba-267">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-268">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-269">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-269">String</span></span>|  
|<span data-ttu-id="8c7ba-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-271">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-271">String</span></span>|  
|<span data-ttu-id="8c7ba-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-272">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-273">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-273">String</span></span>|  
|<span data-ttu-id="8c7ba-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-274">INDEX_CATALOG</span></span>|<span data-ttu-id="8c7ba-275">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-275">String</span></span>|  
|<span data-ttu-id="8c7ba-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="8c7ba-277">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-277">String</span></span>|  
|<span data-ttu-id="8c7ba-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-278">INDEX_NAME</span></span>|<span data-ttu-id="8c7ba-279">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-279">String</span></span>|  
|<span data-ttu-id="8c7ba-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="8c7ba-280">PRIMARY_KEY</span></span>|<span data-ttu-id="8c7ba-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-281">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-282">UNIQUE</span></span>|<span data-ttu-id="8c7ba-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-283">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-284">CLUSTERED</span></span>|<span data-ttu-id="8c7ba-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-285">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-286">TYPE</span></span>|<span data-ttu-id="8c7ba-287">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-287">Int32</span></span>|  
|<span data-ttu-id="8c7ba-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="8c7ba-288">FILL_FACTOR</span></span>|<span data-ttu-id="8c7ba-289">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-289">Int32</span></span>|  
|<span data-ttu-id="8c7ba-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-290">INITIAL_SIZE</span></span>|<span data-ttu-id="8c7ba-291">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-291">Int32</span></span>|  
|<span data-ttu-id="8c7ba-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="8c7ba-292">NULLS</span></span>|<span data-ttu-id="8c7ba-293">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-293">Int32</span></span>|  
|<span data-ttu-id="8c7ba-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="8c7ba-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="8c7ba-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-295">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-296">AUTO_UPDATE</span></span>|<span data-ttu-id="8c7ba-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-297">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-298">NULL_COLLATION</span></span>|<span data-ttu-id="8c7ba-299">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-299">Int32</span></span>|  
|<span data-ttu-id="8c7ba-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="8c7ba-301">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-301">Int64</span></span>|  
|<span data-ttu-id="8c7ba-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-302">COLUMN_NAME</span></span>|<span data-ttu-id="8c7ba-303">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-303">String</span></span>|  
|<span data-ttu-id="8c7ba-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-304">COLUMN_GUID</span></span>|<span data-ttu-id="8c7ba-305">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-305">Guid</span></span>|  
|<span data-ttu-id="8c7ba-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-306">COLUMN_PROPID</span></span>|<span data-ttu-id="8c7ba-307">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-307">Int64</span></span>|  
|<span data-ttu-id="8c7ba-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-308">COLLATION</span></span>|<span data-ttu-id="8c7ba-309">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-309">Int16</span></span>|  
|<span data-ttu-id="8c7ba-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="8c7ba-310">CARDINALITY</span></span>|<span data-ttu-id="8c7ba-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="8c7ba-311">Decimal</span></span>|  
|<span data-ttu-id="8c7ba-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="8c7ba-312">PAGES</span></span>|<span data-ttu-id="8c7ba-313">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-313">Int32</span></span>|  
|<span data-ttu-id="8c7ba-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-314">FILTER_CONDITION</span></span>|<span data-ttu-id="8c7ba-315">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-315">String</span></span>|  
|<span data-ttu-id="8c7ba-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-316">INTEGRATED</span></span>|<span data-ttu-id="8c7ba-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="8c7ba-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="8c7ba-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="8c7ba-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="8c7ba-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="8c7ba-320">資料表</span><span class="sxs-lookup"><span data-stu-id="8c7ba-320">Tables</span></span>  
  
-   <span data-ttu-id="8c7ba-321">資料行</span><span class="sxs-lookup"><span data-stu-id="8c7ba-321">Columns</span></span>  
  
-   <span data-ttu-id="8c7ba-322">程序</span><span class="sxs-lookup"><span data-stu-id="8c7ba-322">Procedures</span></span>  
  
-   <span data-ttu-id="8c7ba-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8c7ba-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="8c7ba-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8c7ba-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="8c7ba-325">檢視</span><span class="sxs-lookup"><span data-stu-id="8c7ba-325">Views</span></span>  
  
-   <span data-ttu-id="8c7ba-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="8c7ba-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="8c7ba-327">資料表</span><span class="sxs-lookup"><span data-stu-id="8c7ba-327">Tables</span></span>  
  
|<span data-ttu-id="8c7ba-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-328">ColumnName</span></span>|<span data-ttu-id="8c7ba-329">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-330">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-331">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-331">String</span></span>|  
|<span data-ttu-id="8c7ba-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-333">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-333">String</span></span>|  
|<span data-ttu-id="8c7ba-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-334">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-335">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-335">String</span></span>|  
|<span data-ttu-id="8c7ba-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-336">TABLE_TYPE</span></span>|<span data-ttu-id="8c7ba-337">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-337">String</span></span>|  
|<span data-ttu-id="8c7ba-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-338">TABLE_GUID</span></span>|<span data-ttu-id="8c7ba-339">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-339">Guid</span></span>|  
|<span data-ttu-id="8c7ba-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-340">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-341">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-341">String</span></span>|  
|<span data-ttu-id="8c7ba-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-342">TABLE_PROPID</span></span>|<span data-ttu-id="8c7ba-343">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-343">Int64</span></span>|  
|<span data-ttu-id="8c7ba-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-344">DATE_CREATED</span></span>|<span data-ttu-id="8c7ba-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-345">DateTime</span></span>|  
|<span data-ttu-id="8c7ba-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-346">DATE_MODIFIED</span></span>|<span data-ttu-id="8c7ba-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8c7ba-348">資料行</span><span class="sxs-lookup"><span data-stu-id="8c7ba-348">Columns</span></span>  
  
|<span data-ttu-id="8c7ba-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-349">ColumnName</span></span>|<span data-ttu-id="8c7ba-350">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-351">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-352">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-352">String</span></span>|  
|<span data-ttu-id="8c7ba-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-354">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-354">String</span></span>|  
|<span data-ttu-id="8c7ba-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-355">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-356">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-356">String</span></span>|  
|<span data-ttu-id="8c7ba-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-357">COLUMN_NAME</span></span>|<span data-ttu-id="8c7ba-358">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-358">String</span></span>|  
|<span data-ttu-id="8c7ba-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-359">COLUMN_GUID</span></span>|<span data-ttu-id="8c7ba-360">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-360">Guid</span></span>|  
|<span data-ttu-id="8c7ba-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-361">COLUMN_PROPID</span></span>|<span data-ttu-id="8c7ba-362">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-362">Int64</span></span>|  
|<span data-ttu-id="8c7ba-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="8c7ba-364">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-364">Int64</span></span>|  
|<span data-ttu-id="8c7ba-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8c7ba-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="8c7ba-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-366">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8c7ba-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="8c7ba-368">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-368">String</span></span>|  
|<span data-ttu-id="8c7ba-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8c7ba-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="8c7ba-370">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-370">Int64</span></span>|  
|<span data-ttu-id="8c7ba-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-371">IS_NULLABLE</span></span>|<span data-ttu-id="8c7ba-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-372">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-373">DATA_TYPE</span></span>|<span data-ttu-id="8c7ba-374">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-374">Int32</span></span>|  
|<span data-ttu-id="8c7ba-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-375">TYPE_GUID</span></span>|<span data-ttu-id="8c7ba-376">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-376">Guid</span></span>|  
|<span data-ttu-id="8c7ba-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8c7ba-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8c7ba-378">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-378">Int64</span></span>|  
|<span data-ttu-id="8c7ba-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8c7ba-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8c7ba-380">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-380">Int64</span></span>|  
|<span data-ttu-id="8c7ba-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8c7ba-382">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-382">Int32</span></span>|  
|<span data-ttu-id="8c7ba-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="8c7ba-384">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-384">Int16</span></span>|  
|<span data-ttu-id="8c7ba-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="8c7ba-386">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-386">Int64</span></span>|  
|<span data-ttu-id="8c7ba-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="8c7ba-388">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-388">String</span></span>|  
|<span data-ttu-id="8c7ba-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="8c7ba-390">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-390">String</span></span>|  
|<span data-ttu-id="8c7ba-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="8c7ba-392">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-392">String</span></span>|  
|<span data-ttu-id="8c7ba-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="8c7ba-394">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-394">String</span></span>|  
|<span data-ttu-id="8c7ba-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="8c7ba-396">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-396">String</span></span>|  
|<span data-ttu-id="8c7ba-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-397">COLLATION_NAME</span></span>|<span data-ttu-id="8c7ba-398">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-398">String</span></span>|  
|<span data-ttu-id="8c7ba-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="8c7ba-400">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-400">String</span></span>|  
|<span data-ttu-id="8c7ba-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="8c7ba-402">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-402">String</span></span>|  
|<span data-ttu-id="8c7ba-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-403">DOMAIN_NAME</span></span>|<span data-ttu-id="8c7ba-404">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-404">String</span></span>|  
|<span data-ttu-id="8c7ba-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-405">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-406">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8c7ba-407">程序</span><span class="sxs-lookup"><span data-stu-id="8c7ba-407">Procedures</span></span>  
  
|<span data-ttu-id="8c7ba-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-408">ColumnName</span></span>|<span data-ttu-id="8c7ba-409">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8c7ba-411">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-411">String</span></span>|  
|<span data-ttu-id="8c7ba-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-413">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-413">String</span></span>|  
|<span data-ttu-id="8c7ba-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="8c7ba-415">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-415">String</span></span>|  
|<span data-ttu-id="8c7ba-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8c7ba-417">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-417">Int16</span></span>|  
|<span data-ttu-id="8c7ba-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="8c7ba-419">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-419">String</span></span>|  
|<span data-ttu-id="8c7ba-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-420">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-421">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-421">String</span></span>|  
|<span data-ttu-id="8c7ba-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-422">DATE_CREATED</span></span>|<span data-ttu-id="8c7ba-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-423">DateTime</span></span>|  
|<span data-ttu-id="8c7ba-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-424">DATE_MODIFIED</span></span>|<span data-ttu-id="8c7ba-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="8c7ba-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8c7ba-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="8c7ba-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-427">ColumnName</span></span>|<span data-ttu-id="8c7ba-428">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8c7ba-430">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-430">String</span></span>|  
|<span data-ttu-id="8c7ba-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-432">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-432">String</span></span>|  
|<span data-ttu-id="8c7ba-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="8c7ba-434">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-434">String</span></span>|  
|<span data-ttu-id="8c7ba-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-435">COLUMN_NAME</span></span>|<span data-ttu-id="8c7ba-436">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-436">String</span></span>|  
|<span data-ttu-id="8c7ba-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-437">COLUMN_GUID</span></span>|<span data-ttu-id="8c7ba-438">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-438">Guid</span></span>|  
|<span data-ttu-id="8c7ba-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-439">COLUMN_PROPID</span></span>|<span data-ttu-id="8c7ba-440">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-440">Int64</span></span>|  
|<span data-ttu-id="8c7ba-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="8c7ba-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="8c7ba-442">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-442">Int64</span></span>|  
|<span data-ttu-id="8c7ba-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="8c7ba-444">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-444">Int64</span></span>|  
|<span data-ttu-id="8c7ba-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-445">IS_NULLABLE</span></span>|<span data-ttu-id="8c7ba-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-446">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-447">DATA_TYPE</span></span>|<span data-ttu-id="8c7ba-448">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-448">Int32</span></span>|  
|<span data-ttu-id="8c7ba-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-449">TYPE_GUID</span></span>|<span data-ttu-id="8c7ba-450">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-450">Guid</span></span>|  
|<span data-ttu-id="8c7ba-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8c7ba-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8c7ba-452">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-452">Int64</span></span>|  
|<span data-ttu-id="8c7ba-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8c7ba-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8c7ba-454">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-454">Int64</span></span>|  
|<span data-ttu-id="8c7ba-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8c7ba-456">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-456">Int32</span></span>|  
|<span data-ttu-id="8c7ba-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="8c7ba-458">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-458">Int16</span></span>|  
|<span data-ttu-id="8c7ba-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-459">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-460">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-460">String</span></span>|  
|<span data-ttu-id="8c7ba-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="8c7ba-461">OVERLOAD</span></span>|<span data-ttu-id="8c7ba-462">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="8c7ba-463">檢視</span><span class="sxs-lookup"><span data-stu-id="8c7ba-463">Views</span></span>  
  
|<span data-ttu-id="8c7ba-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-464">ColumnName</span></span>|<span data-ttu-id="8c7ba-465">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-466">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-467">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-467">String</span></span>|  
|<span data-ttu-id="8c7ba-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-469">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-469">String</span></span>|  
|<span data-ttu-id="8c7ba-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-470">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-471">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-471">String</span></span>|  
|<span data-ttu-id="8c7ba-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="8c7ba-473">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-473">String</span></span>|  
|<span data-ttu-id="8c7ba-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-474">CHECK_OPTION</span></span>|<span data-ttu-id="8c7ba-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-475">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-476">IS_UPDATABLE</span></span>|<span data-ttu-id="8c7ba-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-477">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-478">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-479">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-479">String</span></span>|  
|<span data-ttu-id="8c7ba-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-480">DATE_CREATED</span></span>|<span data-ttu-id="8c7ba-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-481">DateTime</span></span>|  
|<span data-ttu-id="8c7ba-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-482">DATE_MODIFIED</span></span>|<span data-ttu-id="8c7ba-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8c7ba-484">Indexes</span><span class="sxs-lookup"><span data-stu-id="8c7ba-484">Indexes</span></span>  
  
|<span data-ttu-id="8c7ba-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-485">ColumnName</span></span>|<span data-ttu-id="8c7ba-486">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-487">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-488">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-488">String</span></span>|  
|<span data-ttu-id="8c7ba-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-490">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-490">String</span></span>|  
|<span data-ttu-id="8c7ba-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-491">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-492">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-492">String</span></span>|  
|<span data-ttu-id="8c7ba-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-493">INDEX_CATALOG</span></span>|<span data-ttu-id="8c7ba-494">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-494">String</span></span>|  
|<span data-ttu-id="8c7ba-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="8c7ba-496">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-496">String</span></span>|  
|<span data-ttu-id="8c7ba-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-497">INDEX_NAME</span></span>|<span data-ttu-id="8c7ba-498">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-498">String</span></span>|  
|<span data-ttu-id="8c7ba-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="8c7ba-499">PRIMARY_KEY</span></span>|<span data-ttu-id="8c7ba-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-500">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-501">UNIQUE</span></span>|<span data-ttu-id="8c7ba-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-502">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-503">CLUSTERED</span></span>|<span data-ttu-id="8c7ba-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-504">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-505">TYPE</span></span>|<span data-ttu-id="8c7ba-506">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-506">Int32</span></span>|  
|<span data-ttu-id="8c7ba-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="8c7ba-507">FILL_FACTOR</span></span>|<span data-ttu-id="8c7ba-508">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-508">Int32</span></span>|  
|<span data-ttu-id="8c7ba-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-509">INITIAL_SIZE</span></span>|<span data-ttu-id="8c7ba-510">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-510">Int32</span></span>|  
|<span data-ttu-id="8c7ba-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="8c7ba-511">NULLS</span></span>|<span data-ttu-id="8c7ba-512">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-512">Int32</span></span>|  
|<span data-ttu-id="8c7ba-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="8c7ba-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="8c7ba-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-514">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-515">AUTO_UPDATE</span></span>|<span data-ttu-id="8c7ba-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-516">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-517">NULL_COLLATION</span></span>|<span data-ttu-id="8c7ba-518">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-518">Int32</span></span>|  
|<span data-ttu-id="8c7ba-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="8c7ba-520">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-520">Int64</span></span>|  
|<span data-ttu-id="8c7ba-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-521">COLUMN_NAME</span></span>|<span data-ttu-id="8c7ba-522">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-522">String</span></span>|  
|<span data-ttu-id="8c7ba-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-523">COLUMN_GUID</span></span>|<span data-ttu-id="8c7ba-524">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-524">Guid</span></span>|  
|<span data-ttu-id="8c7ba-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-525">COLUMN_PROPID</span></span>|<span data-ttu-id="8c7ba-526">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-526">Int64</span></span>|  
|<span data-ttu-id="8c7ba-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-527">COLLATION</span></span>|<span data-ttu-id="8c7ba-528">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-528">Int16</span></span>|  
|<span data-ttu-id="8c7ba-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="8c7ba-529">CARDINALITY</span></span>|<span data-ttu-id="8c7ba-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="8c7ba-530">Decimal</span></span>|  
|<span data-ttu-id="8c7ba-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="8c7ba-531">PAGES</span></span>|<span data-ttu-id="8c7ba-532">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-532">Int32</span></span>|  
|<span data-ttu-id="8c7ba-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-533">FILTER_CONDITION</span></span>|<span data-ttu-id="8c7ba-534">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-534">String</span></span>|  
|<span data-ttu-id="8c7ba-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-535">INTEGRATED</span></span>|<span data-ttu-id="8c7ba-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="8c7ba-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="8c7ba-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="8c7ba-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="8c7ba-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="8c7ba-539">資料表</span><span class="sxs-lookup"><span data-stu-id="8c7ba-539">Tables</span></span>  
  
-   <span data-ttu-id="8c7ba-540">資料行</span><span class="sxs-lookup"><span data-stu-id="8c7ba-540">Columns</span></span>  
  
-   <span data-ttu-id="8c7ba-541">程序</span><span class="sxs-lookup"><span data-stu-id="8c7ba-541">Procedures</span></span>  
  
-   <span data-ttu-id="8c7ba-542">檢視</span><span class="sxs-lookup"><span data-stu-id="8c7ba-542">Views</span></span>  
  
-   <span data-ttu-id="8c7ba-543">Indexes</span><span class="sxs-lookup"><span data-stu-id="8c7ba-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="8c7ba-544">資料表</span><span class="sxs-lookup"><span data-stu-id="8c7ba-544">Tables</span></span>  
  
|<span data-ttu-id="8c7ba-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-545">ColumnName</span></span>|<span data-ttu-id="8c7ba-546">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-547">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-548">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-548">String</span></span>|  
|<span data-ttu-id="8c7ba-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-550">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-550">String</span></span>|  
|<span data-ttu-id="8c7ba-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-551">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-552">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-552">String</span></span>|  
|<span data-ttu-id="8c7ba-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-553">TABLE_TYPE</span></span>|<span data-ttu-id="8c7ba-554">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-554">String</span></span>|  
|<span data-ttu-id="8c7ba-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-555">TABLE_GUID</span></span>|<span data-ttu-id="8c7ba-556">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-556">Guid</span></span>|  
|<span data-ttu-id="8c7ba-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-557">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-558">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-558">String</span></span>|  
|<span data-ttu-id="8c7ba-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-559">TABLE_PROPID</span></span>|<span data-ttu-id="8c7ba-560">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-560">Int64</span></span>|  
|<span data-ttu-id="8c7ba-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-561">DATE_CREATED</span></span>|<span data-ttu-id="8c7ba-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-562">DateTime</span></span>|  
|<span data-ttu-id="8c7ba-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-563">DATE_MODIFIED</span></span>|<span data-ttu-id="8c7ba-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8c7ba-565">資料行</span><span class="sxs-lookup"><span data-stu-id="8c7ba-565">Columns</span></span>  
  
|<span data-ttu-id="8c7ba-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-566">ColumnName</span></span>|<span data-ttu-id="8c7ba-567">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-568">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-569">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-569">String</span></span>|  
|<span data-ttu-id="8c7ba-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-571">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-571">String</span></span>|  
|<span data-ttu-id="8c7ba-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-572">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-573">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-573">String</span></span>|  
|<span data-ttu-id="8c7ba-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-574">COLUMN_NAME</span></span>|<span data-ttu-id="8c7ba-575">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-575">String</span></span>|  
|<span data-ttu-id="8c7ba-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-576">COLUMN_GUID</span></span>|<span data-ttu-id="8c7ba-577">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-577">Guid</span></span>|  
|<span data-ttu-id="8c7ba-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-578">COLUMN_PROPID</span></span>|<span data-ttu-id="8c7ba-579">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-579">Int64</span></span>|  
|<span data-ttu-id="8c7ba-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="8c7ba-581">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-581">Int64</span></span>|  
|<span data-ttu-id="8c7ba-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8c7ba-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="8c7ba-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-583">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8c7ba-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="8c7ba-585">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-585">String</span></span>|  
|<span data-ttu-id="8c7ba-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8c7ba-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="8c7ba-587">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-587">Int64</span></span>|  
|<span data-ttu-id="8c7ba-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-588">IS_NULLABLE</span></span>|<span data-ttu-id="8c7ba-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-589">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-590">DATA_TYPE</span></span>|<span data-ttu-id="8c7ba-591">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-591">Int32</span></span>|  
|<span data-ttu-id="8c7ba-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-592">TYPE_GUID</span></span>|<span data-ttu-id="8c7ba-593">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-593">Guid</span></span>|  
|<span data-ttu-id="8c7ba-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8c7ba-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8c7ba-595">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-595">Int64</span></span>|  
|<span data-ttu-id="8c7ba-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8c7ba-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8c7ba-597">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-597">Int64</span></span>|  
|<span data-ttu-id="8c7ba-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8c7ba-599">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-599">Int32</span></span>|  
|<span data-ttu-id="8c7ba-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="8c7ba-601">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-601">Int16</span></span>|  
|<span data-ttu-id="8c7ba-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="8c7ba-603">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-603">Int64</span></span>|  
|<span data-ttu-id="8c7ba-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="8c7ba-605">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-605">String</span></span>|  
|<span data-ttu-id="8c7ba-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="8c7ba-607">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-607">String</span></span>|  
|<span data-ttu-id="8c7ba-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="8c7ba-609">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-609">String</span></span>|  
|<span data-ttu-id="8c7ba-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="8c7ba-611">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-611">String</span></span>|  
|<span data-ttu-id="8c7ba-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="8c7ba-613">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-613">String</span></span>|  
|<span data-ttu-id="8c7ba-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-614">COLLATION_NAME</span></span>|<span data-ttu-id="8c7ba-615">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-615">String</span></span>|  
|<span data-ttu-id="8c7ba-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="8c7ba-617">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-617">String</span></span>|  
|<span data-ttu-id="8c7ba-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="8c7ba-619">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-619">String</span></span>|  
|<span data-ttu-id="8c7ba-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-620">DOMAIN_NAME</span></span>|<span data-ttu-id="8c7ba-621">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-621">String</span></span>|  
|<span data-ttu-id="8c7ba-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-622">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-623">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8c7ba-624">程序</span><span class="sxs-lookup"><span data-stu-id="8c7ba-624">Procedures</span></span>  
  
|<span data-ttu-id="8c7ba-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-625">ColumnName</span></span>|<span data-ttu-id="8c7ba-626">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8c7ba-628">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-628">String</span></span>|  
|<span data-ttu-id="8c7ba-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-630">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-630">String</span></span>|  
|<span data-ttu-id="8c7ba-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="8c7ba-632">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-632">String</span></span>|  
|<span data-ttu-id="8c7ba-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8c7ba-634">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-634">Int16</span></span>|  
|<span data-ttu-id="8c7ba-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="8c7ba-636">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-636">String</span></span>|  
|<span data-ttu-id="8c7ba-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-637">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-638">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-638">String</span></span>|  
|<span data-ttu-id="8c7ba-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-639">DATE_CREATED</span></span>|<span data-ttu-id="8c7ba-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-640">DateTime</span></span>|  
|<span data-ttu-id="8c7ba-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-641">DATE_MODIFIED</span></span>|<span data-ttu-id="8c7ba-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="8c7ba-643">檢視</span><span class="sxs-lookup"><span data-stu-id="8c7ba-643">Views</span></span>  
  
|<span data-ttu-id="8c7ba-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-644">ColumnName</span></span>|<span data-ttu-id="8c7ba-645">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-646">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-647">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-647">String</span></span>|  
|<span data-ttu-id="8c7ba-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-649">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-649">String</span></span>|  
|<span data-ttu-id="8c7ba-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-650">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-651">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-651">String</span></span>|  
|<span data-ttu-id="8c7ba-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="8c7ba-653">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-653">String</span></span>|  
|<span data-ttu-id="8c7ba-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-654">CHECK_OPTION</span></span>|<span data-ttu-id="8c7ba-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-655">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-656">IS_UPDATABLE</span></span>|<span data-ttu-id="8c7ba-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-657">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-658">DESCRIPTION</span></span>|<span data-ttu-id="8c7ba-659">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-659">String</span></span>|  
|<span data-ttu-id="8c7ba-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-660">DATE_CREATED</span></span>|<span data-ttu-id="8c7ba-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-661">DateTime</span></span>|  
|<span data-ttu-id="8c7ba-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-662">DATE_MODIFIED</span></span>|<span data-ttu-id="8c7ba-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7ba-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8c7ba-664">Indexes</span><span class="sxs-lookup"><span data-stu-id="8c7ba-664">Indexes</span></span>  
  
|<span data-ttu-id="8c7ba-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8c7ba-665">ColumnName</span></span>|<span data-ttu-id="8c7ba-666">DataType</span><span class="sxs-lookup"><span data-stu-id="8c7ba-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8c7ba-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-667">TABLE_CATALOG</span></span>|<span data-ttu-id="8c7ba-668">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-668">String</span></span>|  
|<span data-ttu-id="8c7ba-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="8c7ba-670">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-670">String</span></span>|  
|<span data-ttu-id="8c7ba-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-671">TABLE_NAME</span></span>|<span data-ttu-id="8c7ba-672">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-672">String</span></span>|  
|<span data-ttu-id="8c7ba-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8c7ba-673">INDEX_CATALOG</span></span>|<span data-ttu-id="8c7ba-674">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-674">String</span></span>|  
|<span data-ttu-id="8c7ba-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8c7ba-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="8c7ba-676">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-676">String</span></span>|  
|<span data-ttu-id="8c7ba-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-677">INDEX_NAME</span></span>|<span data-ttu-id="8c7ba-678">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-678">String</span></span>|  
|<span data-ttu-id="8c7ba-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="8c7ba-679">PRIMARY_KEY</span></span>|<span data-ttu-id="8c7ba-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-680">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-681">UNIQUE</span></span>|<span data-ttu-id="8c7ba-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-682">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-683">CLUSTERED</span></span>|<span data-ttu-id="8c7ba-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-684">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-685">TYPE</span></span>|<span data-ttu-id="8c7ba-686">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-686">Int32</span></span>|  
|<span data-ttu-id="8c7ba-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="8c7ba-687">FILL_FACTOR</span></span>|<span data-ttu-id="8c7ba-688">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-688">Int32</span></span>|  
|<span data-ttu-id="8c7ba-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-689">INITIAL_SIZE</span></span>|<span data-ttu-id="8c7ba-690">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-690">Int32</span></span>|  
|<span data-ttu-id="8c7ba-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="8c7ba-691">NULLS</span></span>|<span data-ttu-id="8c7ba-692">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-692">Int32</span></span>|  
|<span data-ttu-id="8c7ba-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="8c7ba-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="8c7ba-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-694">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="8c7ba-695">AUTO_UPDATE</span></span>|<span data-ttu-id="8c7ba-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-696">Boolean</span></span>|  
|<span data-ttu-id="8c7ba-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-697">NULL_COLLATION</span></span>|<span data-ttu-id="8c7ba-698">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-698">Int32</span></span>|  
|<span data-ttu-id="8c7ba-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="8c7ba-700">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-700">Int64</span></span>|  
|<span data-ttu-id="8c7ba-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8c7ba-701">COLUMN_NAME</span></span>|<span data-ttu-id="8c7ba-702">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-702">String</span></span>|  
|<span data-ttu-id="8c7ba-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-703">COLUMN_GUID</span></span>|<span data-ttu-id="8c7ba-704">Guid</span><span class="sxs-lookup"><span data-stu-id="8c7ba-704">Guid</span></span>|  
|<span data-ttu-id="8c7ba-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8c7ba-705">COLUMN_PROPID</span></span>|<span data-ttu-id="8c7ba-706">Int64</span><span class="sxs-lookup"><span data-stu-id="8c7ba-706">Int64</span></span>|  
|<span data-ttu-id="8c7ba-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-707">COLLATION</span></span>|<span data-ttu-id="8c7ba-708">Int16</span><span class="sxs-lookup"><span data-stu-id="8c7ba-708">Int16</span></span>|  
|<span data-ttu-id="8c7ba-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="8c7ba-709">CARDINALITY</span></span>|<span data-ttu-id="8c7ba-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="8c7ba-710">Decimal</span></span>|  
|<span data-ttu-id="8c7ba-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="8c7ba-711">PAGES</span></span>|<span data-ttu-id="8c7ba-712">Int32</span><span class="sxs-lookup"><span data-stu-id="8c7ba-712">Int32</span></span>|  
|<span data-ttu-id="8c7ba-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="8c7ba-713">FILTER_CONDITION</span></span>|<span data-ttu-id="8c7ba-714">String</span><span class="sxs-lookup"><span data-stu-id="8c7ba-714">String</span></span>|  
|<span data-ttu-id="8c7ba-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="8c7ba-715">INTEGRATED</span></span>|<span data-ttu-id="8c7ba-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="8c7ba-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c7ba-717">請參閱</span><span class="sxs-lookup"><span data-stu-id="8c7ba-717">See Also</span></span>  
 [<span data-ttu-id="8c7ba-718">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="8c7ba-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
