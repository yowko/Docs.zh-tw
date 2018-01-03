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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e120ea532b6da455e31ce7345b6c4b2be1ec975f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="6c467-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="6c467-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="6c467-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="6c467-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="6c467-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="6c467-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="6c467-105">Microsoft SQL Server OLE DB 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="6c467-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="6c467-106">資料表</span><span class="sxs-lookup"><span data-stu-id="6c467-106">Tables</span></span>  
  
-   <span data-ttu-id="6c467-107">資料行</span><span class="sxs-lookup"><span data-stu-id="6c467-107">Columns</span></span>  
  
-   <span data-ttu-id="6c467-108">程序</span><span class="sxs-lookup"><span data-stu-id="6c467-108">Procedures</span></span>  
  
-   <span data-ttu-id="6c467-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6c467-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="6c467-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="6c467-110">Catalog</span></span>  
  
-   <span data-ttu-id="6c467-111">Indexes</span><span class="sxs-lookup"><span data-stu-id="6c467-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6c467-112">資料表</span><span class="sxs-lookup"><span data-stu-id="6c467-112">Tables</span></span>  
  
|<span data-ttu-id="6c467-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-113">ColumnName</span></span>|<span data-ttu-id="6c467-114">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-115">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-116">String</span><span class="sxs-lookup"><span data-stu-id="6c467-116">String</span></span>|  
|<span data-ttu-id="6c467-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-118">String</span><span class="sxs-lookup"><span data-stu-id="6c467-118">String</span></span>|  
|<span data-ttu-id="6c467-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-119">TABLE_NAME</span></span>|<span data-ttu-id="6c467-120">String</span><span class="sxs-lookup"><span data-stu-id="6c467-120">String</span></span>|  
|<span data-ttu-id="6c467-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-121">TABLE_TYPE</span></span>|<span data-ttu-id="6c467-122">String</span><span class="sxs-lookup"><span data-stu-id="6c467-122">String</span></span>|  
|<span data-ttu-id="6c467-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-123">TABLE_GUID</span></span>|<span data-ttu-id="6c467-124">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-124">Guid</span></span>|  
|<span data-ttu-id="6c467-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-125">DESCRIPTION</span></span>|<span data-ttu-id="6c467-126">String</span><span class="sxs-lookup"><span data-stu-id="6c467-126">String</span></span>|  
|<span data-ttu-id="6c467-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6c467-127">TABLE_PROPID</span></span>|<span data-ttu-id="6c467-128">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-128">Int64</span></span>|  
|<span data-ttu-id="6c467-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6c467-129">DATE_CREATED</span></span>|<span data-ttu-id="6c467-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-130">DateTime</span></span>|  
|<span data-ttu-id="6c467-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6c467-131">DATE_MODIFIED</span></span>|<span data-ttu-id="6c467-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6c467-133">資料行</span><span class="sxs-lookup"><span data-stu-id="6c467-133">Columns</span></span>  
  
|<span data-ttu-id="6c467-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-134">ColumnName</span></span>|<span data-ttu-id="6c467-135">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-136">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-137">String</span><span class="sxs-lookup"><span data-stu-id="6c467-137">String</span></span>|  
|<span data-ttu-id="6c467-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-139">String</span><span class="sxs-lookup"><span data-stu-id="6c467-139">String</span></span>|  
|<span data-ttu-id="6c467-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-140">TABLE_NAME</span></span>|<span data-ttu-id="6c467-141">String</span><span class="sxs-lookup"><span data-stu-id="6c467-141">String</span></span>|  
|<span data-ttu-id="6c467-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-142">COLUMN_NAME</span></span>|<span data-ttu-id="6c467-143">String</span><span class="sxs-lookup"><span data-stu-id="6c467-143">String</span></span>|  
|<span data-ttu-id="6c467-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-144">COLUMN_GUID</span></span>|<span data-ttu-id="6c467-145">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-145">Guid</span></span>|  
|<span data-ttu-id="6c467-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6c467-146">COLUMN_PROPID</span></span>|<span data-ttu-id="6c467-147">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-147">Int64</span></span>|  
|<span data-ttu-id="6c467-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6c467-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="6c467-149">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-149">Int64</span></span>|  
|<span data-ttu-id="6c467-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6c467-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6c467-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-151">Boolean</span></span>|  
|<span data-ttu-id="6c467-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6c467-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6c467-153">String</span><span class="sxs-lookup"><span data-stu-id="6c467-153">String</span></span>|  
|<span data-ttu-id="6c467-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6c467-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="6c467-155">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-155">Int64</span></span>|  
|<span data-ttu-id="6c467-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6c467-156">IS_NULLABLE</span></span>|<span data-ttu-id="6c467-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-157">Boolean</span></span>|  
|<span data-ttu-id="6c467-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-158">DATA_TYPE</span></span>|<span data-ttu-id="6c467-159">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-159">Int32</span></span>|  
|<span data-ttu-id="6c467-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-160">TYPE_GUID</span></span>|<span data-ttu-id="6c467-161">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-161">Guid</span></span>|  
|<span data-ttu-id="6c467-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6c467-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6c467-163">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-163">Int64</span></span>|  
|<span data-ttu-id="6c467-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6c467-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6c467-165">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-165">Int64</span></span>|  
|<span data-ttu-id="6c467-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6c467-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6c467-167">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-167">Int32</span></span>|  
|<span data-ttu-id="6c467-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6c467-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="6c467-169">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-169">Int16</span></span>|  
|<span data-ttu-id="6c467-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6c467-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="6c467-171">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-171">Int64</span></span>|  
|<span data-ttu-id="6c467-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6c467-173">String</span><span class="sxs-lookup"><span data-stu-id="6c467-173">String</span></span>|  
|<span data-ttu-id="6c467-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6c467-175">String</span><span class="sxs-lookup"><span data-stu-id="6c467-175">String</span></span>|  
|<span data-ttu-id="6c467-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6c467-177">String</span><span class="sxs-lookup"><span data-stu-id="6c467-177">String</span></span>|  
|<span data-ttu-id="6c467-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="6c467-179">String</span><span class="sxs-lookup"><span data-stu-id="6c467-179">String</span></span>|  
|<span data-ttu-id="6c467-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6c467-181">String</span><span class="sxs-lookup"><span data-stu-id="6c467-181">String</span></span>|  
|<span data-ttu-id="6c467-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-182">COLLATION_NAME</span></span>|<span data-ttu-id="6c467-183">String</span><span class="sxs-lookup"><span data-stu-id="6c467-183">String</span></span>|  
|<span data-ttu-id="6c467-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6c467-185">String</span><span class="sxs-lookup"><span data-stu-id="6c467-185">String</span></span>|  
|<span data-ttu-id="6c467-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6c467-187">String</span><span class="sxs-lookup"><span data-stu-id="6c467-187">String</span></span>|  
|<span data-ttu-id="6c467-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-188">DOMAIN_NAME</span></span>|<span data-ttu-id="6c467-189">String</span><span class="sxs-lookup"><span data-stu-id="6c467-189">String</span></span>|  
|<span data-ttu-id="6c467-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-190">DESCRIPTION</span></span>|<span data-ttu-id="6c467-191">String</span><span class="sxs-lookup"><span data-stu-id="6c467-191">String</span></span>|  
|<span data-ttu-id="6c467-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="6c467-192">COLUMN_LCID</span></span>|<span data-ttu-id="6c467-193">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-193">Int32</span></span>|  
|<span data-ttu-id="6c467-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="6c467-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="6c467-195">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-195">Int32</span></span>|  
|<span data-ttu-id="6c467-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="6c467-196">COLUMN_SORTID</span></span>|<span data-ttu-id="6c467-197">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-197">Int32</span></span>|  
|<span data-ttu-id="6c467-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="6c467-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="6c467-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="6c467-199">Byte[]</span></span>|  
|<span data-ttu-id="6c467-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="6c467-200">IS_COMPUTED</span></span>|<span data-ttu-id="6c467-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6c467-202">程序</span><span class="sxs-lookup"><span data-stu-id="6c467-202">Procedures</span></span>  
  
|<span data-ttu-id="6c467-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-203">ColumnName</span></span>|<span data-ttu-id="6c467-204">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6c467-206">String</span><span class="sxs-lookup"><span data-stu-id="6c467-206">String</span></span>|  
|<span data-ttu-id="6c467-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6c467-208">String</span><span class="sxs-lookup"><span data-stu-id="6c467-208">String</span></span>|  
|<span data-ttu-id="6c467-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="6c467-210">String</span><span class="sxs-lookup"><span data-stu-id="6c467-210">String</span></span>|  
|<span data-ttu-id="6c467-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6c467-212">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-212">Int16</span></span>|  
|<span data-ttu-id="6c467-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6c467-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6c467-214">String</span><span class="sxs-lookup"><span data-stu-id="6c467-214">String</span></span>|  
|<span data-ttu-id="6c467-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-215">DESCRIPTION</span></span>|<span data-ttu-id="6c467-216">String</span><span class="sxs-lookup"><span data-stu-id="6c467-216">String</span></span>|  
|<span data-ttu-id="6c467-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6c467-217">DATE_CREATED</span></span>|<span data-ttu-id="6c467-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-218">DateTime</span></span>|  
|<span data-ttu-id="6c467-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6c467-219">DATE_MODIFIED</span></span>|<span data-ttu-id="6c467-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="6c467-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6c467-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="6c467-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-222">ColumnName</span></span>|<span data-ttu-id="6c467-223">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6c467-225">String</span><span class="sxs-lookup"><span data-stu-id="6c467-225">String</span></span>|  
|<span data-ttu-id="6c467-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6c467-227">String</span><span class="sxs-lookup"><span data-stu-id="6c467-227">String</span></span>|  
|<span data-ttu-id="6c467-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="6c467-229">String</span><span class="sxs-lookup"><span data-stu-id="6c467-229">String</span></span>|  
|<span data-ttu-id="6c467-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-230">PARAMETER_NAME</span></span>|<span data-ttu-id="6c467-231">String</span><span class="sxs-lookup"><span data-stu-id="6c467-231">String</span></span>|  
|<span data-ttu-id="6c467-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6c467-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="6c467-233">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-233">Int32</span></span>|  
|<span data-ttu-id="6c467-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="6c467-235">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-235">Int32</span></span>|  
|<span data-ttu-id="6c467-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6c467-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="6c467-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-237">Boolean</span></span>|  
|<span data-ttu-id="6c467-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6c467-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="6c467-239">String</span><span class="sxs-lookup"><span data-stu-id="6c467-239">String</span></span>|  
|<span data-ttu-id="6c467-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6c467-240">IS_NULLABLE</span></span>|<span data-ttu-id="6c467-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-241">Boolean</span></span>|  
|<span data-ttu-id="6c467-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-242">DATA_TYPE</span></span>|<span data-ttu-id="6c467-243">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-243">Int32</span></span>|  
|<span data-ttu-id="6c467-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6c467-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6c467-245">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-245">Int64</span></span>|  
|<span data-ttu-id="6c467-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6c467-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6c467-247">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-247">Int64</span></span>|  
|<span data-ttu-id="6c467-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6c467-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6c467-249">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-249">Int32</span></span>|  
|<span data-ttu-id="6c467-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6c467-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="6c467-251">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-251">Int16</span></span>|  
|<span data-ttu-id="6c467-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-252">DESCRIPTION</span></span>|<span data-ttu-id="6c467-253">String</span><span class="sxs-lookup"><span data-stu-id="6c467-253">String</span></span>|  
|<span data-ttu-id="6c467-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-254">TYPE_NAME</span></span>|<span data-ttu-id="6c467-255">String</span><span class="sxs-lookup"><span data-stu-id="6c467-255">String</span></span>|  
|<span data-ttu-id="6c467-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="6c467-257">String</span><span class="sxs-lookup"><span data-stu-id="6c467-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="6c467-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="6c467-258">Catalog</span></span>  
  
|<span data-ttu-id="6c467-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-259">ColumnName</span></span>|<span data-ttu-id="6c467-260">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-261">CATALOG_NAME</span></span>|<span data-ttu-id="6c467-262">String</span><span class="sxs-lookup"><span data-stu-id="6c467-262">String</span></span>|  
|<span data-ttu-id="6c467-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-263">DESCRIPTION</span></span>|<span data-ttu-id="6c467-264">String</span><span class="sxs-lookup"><span data-stu-id="6c467-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6c467-265">Indexes</span><span class="sxs-lookup"><span data-stu-id="6c467-265">Indexes</span></span>  
  
|<span data-ttu-id="6c467-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-266">ColumnName</span></span>|<span data-ttu-id="6c467-267">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-268">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-269">String</span><span class="sxs-lookup"><span data-stu-id="6c467-269">String</span></span>|  
|<span data-ttu-id="6c467-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-271">String</span><span class="sxs-lookup"><span data-stu-id="6c467-271">String</span></span>|  
|<span data-ttu-id="6c467-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-272">TABLE_NAME</span></span>|<span data-ttu-id="6c467-273">String</span><span class="sxs-lookup"><span data-stu-id="6c467-273">String</span></span>|  
|<span data-ttu-id="6c467-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-274">INDEX_CATALOG</span></span>|<span data-ttu-id="6c467-275">String</span><span class="sxs-lookup"><span data-stu-id="6c467-275">String</span></span>|  
|<span data-ttu-id="6c467-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="6c467-277">String</span><span class="sxs-lookup"><span data-stu-id="6c467-277">String</span></span>|  
|<span data-ttu-id="6c467-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-278">INDEX_NAME</span></span>|<span data-ttu-id="6c467-279">String</span><span class="sxs-lookup"><span data-stu-id="6c467-279">String</span></span>|  
|<span data-ttu-id="6c467-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6c467-280">PRIMARY_KEY</span></span>|<span data-ttu-id="6c467-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-281">Boolean</span></span>|  
|<span data-ttu-id="6c467-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="6c467-282">UNIQUE</span></span>|<span data-ttu-id="6c467-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-283">Boolean</span></span>|  
|<span data-ttu-id="6c467-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6c467-284">CLUSTERED</span></span>|<span data-ttu-id="6c467-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-285">Boolean</span></span>|  
|<span data-ttu-id="6c467-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-286">TYPE</span></span>|<span data-ttu-id="6c467-287">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-287">Int32</span></span>|  
|<span data-ttu-id="6c467-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6c467-288">FILL_FACTOR</span></span>|<span data-ttu-id="6c467-289">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-289">Int32</span></span>|  
|<span data-ttu-id="6c467-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6c467-290">INITIAL_SIZE</span></span>|<span data-ttu-id="6c467-291">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-291">Int32</span></span>|  
|<span data-ttu-id="6c467-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="6c467-292">NULLS</span></span>|<span data-ttu-id="6c467-293">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-293">Int32</span></span>|  
|<span data-ttu-id="6c467-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6c467-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6c467-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-295">Boolean</span></span>|  
|<span data-ttu-id="6c467-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6c467-296">AUTO_UPDATE</span></span>|<span data-ttu-id="6c467-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-297">Boolean</span></span>|  
|<span data-ttu-id="6c467-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6c467-298">NULL_COLLATION</span></span>|<span data-ttu-id="6c467-299">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-299">Int32</span></span>|  
|<span data-ttu-id="6c467-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6c467-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="6c467-301">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-301">Int64</span></span>|  
|<span data-ttu-id="6c467-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-302">COLUMN_NAME</span></span>|<span data-ttu-id="6c467-303">String</span><span class="sxs-lookup"><span data-stu-id="6c467-303">String</span></span>|  
|<span data-ttu-id="6c467-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-304">COLUMN_GUID</span></span>|<span data-ttu-id="6c467-305">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-305">Guid</span></span>|  
|<span data-ttu-id="6c467-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6c467-306">COLUMN_PROPID</span></span>|<span data-ttu-id="6c467-307">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-307">Int64</span></span>|  
|<span data-ttu-id="6c467-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="6c467-308">COLLATION</span></span>|<span data-ttu-id="6c467-309">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-309">Int16</span></span>|  
|<span data-ttu-id="6c467-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="6c467-310">CARDINALITY</span></span>|<span data-ttu-id="6c467-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="6c467-311">Decimal</span></span>|  
|<span data-ttu-id="6c467-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="6c467-312">PAGES</span></span>|<span data-ttu-id="6c467-313">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-313">Int32</span></span>|  
|<span data-ttu-id="6c467-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6c467-314">FILTER_CONDITION</span></span>|<span data-ttu-id="6c467-315">String</span><span class="sxs-lookup"><span data-stu-id="6c467-315">String</span></span>|  
|<span data-ttu-id="6c467-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="6c467-316">INTEGRATED</span></span>|<span data-ttu-id="6c467-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="6c467-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="6c467-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="6c467-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="6c467-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="6c467-320">資料表</span><span class="sxs-lookup"><span data-stu-id="6c467-320">Tables</span></span>  
  
-   <span data-ttu-id="6c467-321">資料行</span><span class="sxs-lookup"><span data-stu-id="6c467-321">Columns</span></span>  
  
-   <span data-ttu-id="6c467-322">程序</span><span class="sxs-lookup"><span data-stu-id="6c467-322">Procedures</span></span>  
  
-   <span data-ttu-id="6c467-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="6c467-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="6c467-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6c467-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="6c467-325">檢視</span><span class="sxs-lookup"><span data-stu-id="6c467-325">Views</span></span>  
  
-   <span data-ttu-id="6c467-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="6c467-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6c467-327">資料表</span><span class="sxs-lookup"><span data-stu-id="6c467-327">Tables</span></span>  
  
|<span data-ttu-id="6c467-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-328">ColumnName</span></span>|<span data-ttu-id="6c467-329">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-330">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-331">String</span><span class="sxs-lookup"><span data-stu-id="6c467-331">String</span></span>|  
|<span data-ttu-id="6c467-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-333">String</span><span class="sxs-lookup"><span data-stu-id="6c467-333">String</span></span>|  
|<span data-ttu-id="6c467-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-334">TABLE_NAME</span></span>|<span data-ttu-id="6c467-335">String</span><span class="sxs-lookup"><span data-stu-id="6c467-335">String</span></span>|  
|<span data-ttu-id="6c467-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-336">TABLE_TYPE</span></span>|<span data-ttu-id="6c467-337">String</span><span class="sxs-lookup"><span data-stu-id="6c467-337">String</span></span>|  
|<span data-ttu-id="6c467-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-338">TABLE_GUID</span></span>|<span data-ttu-id="6c467-339">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-339">Guid</span></span>|  
|<span data-ttu-id="6c467-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-340">DESCRIPTION</span></span>|<span data-ttu-id="6c467-341">String</span><span class="sxs-lookup"><span data-stu-id="6c467-341">String</span></span>|  
|<span data-ttu-id="6c467-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6c467-342">TABLE_PROPID</span></span>|<span data-ttu-id="6c467-343">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-343">Int64</span></span>|  
|<span data-ttu-id="6c467-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6c467-344">DATE_CREATED</span></span>|<span data-ttu-id="6c467-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-345">DateTime</span></span>|  
|<span data-ttu-id="6c467-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6c467-346">DATE_MODIFIED</span></span>|<span data-ttu-id="6c467-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6c467-348">資料行</span><span class="sxs-lookup"><span data-stu-id="6c467-348">Columns</span></span>  
  
|<span data-ttu-id="6c467-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-349">ColumnName</span></span>|<span data-ttu-id="6c467-350">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-351">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-352">String</span><span class="sxs-lookup"><span data-stu-id="6c467-352">String</span></span>|  
|<span data-ttu-id="6c467-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-354">String</span><span class="sxs-lookup"><span data-stu-id="6c467-354">String</span></span>|  
|<span data-ttu-id="6c467-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-355">TABLE_NAME</span></span>|<span data-ttu-id="6c467-356">String</span><span class="sxs-lookup"><span data-stu-id="6c467-356">String</span></span>|  
|<span data-ttu-id="6c467-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-357">COLUMN_NAME</span></span>|<span data-ttu-id="6c467-358">String</span><span class="sxs-lookup"><span data-stu-id="6c467-358">String</span></span>|  
|<span data-ttu-id="6c467-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-359">COLUMN_GUID</span></span>|<span data-ttu-id="6c467-360">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-360">Guid</span></span>|  
|<span data-ttu-id="6c467-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6c467-361">COLUMN_PROPID</span></span>|<span data-ttu-id="6c467-362">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-362">Int64</span></span>|  
|<span data-ttu-id="6c467-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6c467-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="6c467-364">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-364">Int64</span></span>|  
|<span data-ttu-id="6c467-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6c467-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6c467-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-366">Boolean</span></span>|  
|<span data-ttu-id="6c467-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6c467-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6c467-368">String</span><span class="sxs-lookup"><span data-stu-id="6c467-368">String</span></span>|  
|<span data-ttu-id="6c467-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6c467-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="6c467-370">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-370">Int64</span></span>|  
|<span data-ttu-id="6c467-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6c467-371">IS_NULLABLE</span></span>|<span data-ttu-id="6c467-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-372">Boolean</span></span>|  
|<span data-ttu-id="6c467-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-373">DATA_TYPE</span></span>|<span data-ttu-id="6c467-374">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-374">Int32</span></span>|  
|<span data-ttu-id="6c467-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-375">TYPE_GUID</span></span>|<span data-ttu-id="6c467-376">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-376">Guid</span></span>|  
|<span data-ttu-id="6c467-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6c467-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6c467-378">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-378">Int64</span></span>|  
|<span data-ttu-id="6c467-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6c467-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6c467-380">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-380">Int64</span></span>|  
|<span data-ttu-id="6c467-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6c467-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6c467-382">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-382">Int32</span></span>|  
|<span data-ttu-id="6c467-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6c467-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="6c467-384">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-384">Int16</span></span>|  
|<span data-ttu-id="6c467-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6c467-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="6c467-386">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-386">Int64</span></span>|  
|<span data-ttu-id="6c467-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6c467-388">String</span><span class="sxs-lookup"><span data-stu-id="6c467-388">String</span></span>|  
|<span data-ttu-id="6c467-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6c467-390">String</span><span class="sxs-lookup"><span data-stu-id="6c467-390">String</span></span>|  
|<span data-ttu-id="6c467-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6c467-392">String</span><span class="sxs-lookup"><span data-stu-id="6c467-392">String</span></span>|  
|<span data-ttu-id="6c467-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="6c467-394">String</span><span class="sxs-lookup"><span data-stu-id="6c467-394">String</span></span>|  
|<span data-ttu-id="6c467-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6c467-396">String</span><span class="sxs-lookup"><span data-stu-id="6c467-396">String</span></span>|  
|<span data-ttu-id="6c467-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-397">COLLATION_NAME</span></span>|<span data-ttu-id="6c467-398">String</span><span class="sxs-lookup"><span data-stu-id="6c467-398">String</span></span>|  
|<span data-ttu-id="6c467-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6c467-400">String</span><span class="sxs-lookup"><span data-stu-id="6c467-400">String</span></span>|  
|<span data-ttu-id="6c467-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6c467-402">String</span><span class="sxs-lookup"><span data-stu-id="6c467-402">String</span></span>|  
|<span data-ttu-id="6c467-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-403">DOMAIN_NAME</span></span>|<span data-ttu-id="6c467-404">String</span><span class="sxs-lookup"><span data-stu-id="6c467-404">String</span></span>|  
|<span data-ttu-id="6c467-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-405">DESCRIPTION</span></span>|<span data-ttu-id="6c467-406">String</span><span class="sxs-lookup"><span data-stu-id="6c467-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6c467-407">程序</span><span class="sxs-lookup"><span data-stu-id="6c467-407">Procedures</span></span>  
  
|<span data-ttu-id="6c467-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-408">ColumnName</span></span>|<span data-ttu-id="6c467-409">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6c467-411">String</span><span class="sxs-lookup"><span data-stu-id="6c467-411">String</span></span>|  
|<span data-ttu-id="6c467-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6c467-413">String</span><span class="sxs-lookup"><span data-stu-id="6c467-413">String</span></span>|  
|<span data-ttu-id="6c467-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="6c467-415">String</span><span class="sxs-lookup"><span data-stu-id="6c467-415">String</span></span>|  
|<span data-ttu-id="6c467-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6c467-417">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-417">Int16</span></span>|  
|<span data-ttu-id="6c467-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6c467-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6c467-419">String</span><span class="sxs-lookup"><span data-stu-id="6c467-419">String</span></span>|  
|<span data-ttu-id="6c467-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-420">DESCRIPTION</span></span>|<span data-ttu-id="6c467-421">String</span><span class="sxs-lookup"><span data-stu-id="6c467-421">String</span></span>|  
|<span data-ttu-id="6c467-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6c467-422">DATE_CREATED</span></span>|<span data-ttu-id="6c467-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-423">DateTime</span></span>|  
|<span data-ttu-id="6c467-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6c467-424">DATE_MODIFIED</span></span>|<span data-ttu-id="6c467-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="6c467-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="6c467-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="6c467-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-427">ColumnName</span></span>|<span data-ttu-id="6c467-428">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6c467-430">String</span><span class="sxs-lookup"><span data-stu-id="6c467-430">String</span></span>|  
|<span data-ttu-id="6c467-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6c467-432">String</span><span class="sxs-lookup"><span data-stu-id="6c467-432">String</span></span>|  
|<span data-ttu-id="6c467-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="6c467-434">String</span><span class="sxs-lookup"><span data-stu-id="6c467-434">String</span></span>|  
|<span data-ttu-id="6c467-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-435">COLUMN_NAME</span></span>|<span data-ttu-id="6c467-436">String</span><span class="sxs-lookup"><span data-stu-id="6c467-436">String</span></span>|  
|<span data-ttu-id="6c467-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-437">COLUMN_GUID</span></span>|<span data-ttu-id="6c467-438">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-438">Guid</span></span>|  
|<span data-ttu-id="6c467-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6c467-439">COLUMN_PROPID</span></span>|<span data-ttu-id="6c467-440">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-440">Int64</span></span>|  
|<span data-ttu-id="6c467-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="6c467-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="6c467-442">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-442">Int64</span></span>|  
|<span data-ttu-id="6c467-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6c467-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="6c467-444">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-444">Int64</span></span>|  
|<span data-ttu-id="6c467-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6c467-445">IS_NULLABLE</span></span>|<span data-ttu-id="6c467-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-446">Boolean</span></span>|  
|<span data-ttu-id="6c467-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-447">DATA_TYPE</span></span>|<span data-ttu-id="6c467-448">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-448">Int32</span></span>|  
|<span data-ttu-id="6c467-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-449">TYPE_GUID</span></span>|<span data-ttu-id="6c467-450">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-450">Guid</span></span>|  
|<span data-ttu-id="6c467-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6c467-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6c467-452">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-452">Int64</span></span>|  
|<span data-ttu-id="6c467-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6c467-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6c467-454">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-454">Int64</span></span>|  
|<span data-ttu-id="6c467-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6c467-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6c467-456">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-456">Int32</span></span>|  
|<span data-ttu-id="6c467-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6c467-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="6c467-458">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-458">Int16</span></span>|  
|<span data-ttu-id="6c467-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-459">DESCRIPTION</span></span>|<span data-ttu-id="6c467-460">String</span><span class="sxs-lookup"><span data-stu-id="6c467-460">String</span></span>|  
|<span data-ttu-id="6c467-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="6c467-461">OVERLOAD</span></span>|<span data-ttu-id="6c467-462">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="6c467-463">檢視</span><span class="sxs-lookup"><span data-stu-id="6c467-463">Views</span></span>  
  
|<span data-ttu-id="6c467-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-464">ColumnName</span></span>|<span data-ttu-id="6c467-465">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-466">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-467">String</span><span class="sxs-lookup"><span data-stu-id="6c467-467">String</span></span>|  
|<span data-ttu-id="6c467-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-469">String</span><span class="sxs-lookup"><span data-stu-id="6c467-469">String</span></span>|  
|<span data-ttu-id="6c467-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-470">TABLE_NAME</span></span>|<span data-ttu-id="6c467-471">String</span><span class="sxs-lookup"><span data-stu-id="6c467-471">String</span></span>|  
|<span data-ttu-id="6c467-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6c467-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="6c467-473">String</span><span class="sxs-lookup"><span data-stu-id="6c467-473">String</span></span>|  
|<span data-ttu-id="6c467-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-474">CHECK_OPTION</span></span>|<span data-ttu-id="6c467-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-475">Boolean</span></span>|  
|<span data-ttu-id="6c467-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="6c467-476">IS_UPDATABLE</span></span>|<span data-ttu-id="6c467-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-477">Boolean</span></span>|  
|<span data-ttu-id="6c467-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-478">DESCRIPTION</span></span>|<span data-ttu-id="6c467-479">String</span><span class="sxs-lookup"><span data-stu-id="6c467-479">String</span></span>|  
|<span data-ttu-id="6c467-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6c467-480">DATE_CREATED</span></span>|<span data-ttu-id="6c467-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-481">DateTime</span></span>|  
|<span data-ttu-id="6c467-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6c467-482">DATE_MODIFIED</span></span>|<span data-ttu-id="6c467-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6c467-484">Indexes</span><span class="sxs-lookup"><span data-stu-id="6c467-484">Indexes</span></span>  
  
|<span data-ttu-id="6c467-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-485">ColumnName</span></span>|<span data-ttu-id="6c467-486">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-487">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-488">String</span><span class="sxs-lookup"><span data-stu-id="6c467-488">String</span></span>|  
|<span data-ttu-id="6c467-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-490">String</span><span class="sxs-lookup"><span data-stu-id="6c467-490">String</span></span>|  
|<span data-ttu-id="6c467-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-491">TABLE_NAME</span></span>|<span data-ttu-id="6c467-492">String</span><span class="sxs-lookup"><span data-stu-id="6c467-492">String</span></span>|  
|<span data-ttu-id="6c467-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-493">INDEX_CATALOG</span></span>|<span data-ttu-id="6c467-494">String</span><span class="sxs-lookup"><span data-stu-id="6c467-494">String</span></span>|  
|<span data-ttu-id="6c467-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="6c467-496">String</span><span class="sxs-lookup"><span data-stu-id="6c467-496">String</span></span>|  
|<span data-ttu-id="6c467-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-497">INDEX_NAME</span></span>|<span data-ttu-id="6c467-498">String</span><span class="sxs-lookup"><span data-stu-id="6c467-498">String</span></span>|  
|<span data-ttu-id="6c467-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6c467-499">PRIMARY_KEY</span></span>|<span data-ttu-id="6c467-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-500">Boolean</span></span>|  
|<span data-ttu-id="6c467-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="6c467-501">UNIQUE</span></span>|<span data-ttu-id="6c467-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-502">Boolean</span></span>|  
|<span data-ttu-id="6c467-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6c467-503">CLUSTERED</span></span>|<span data-ttu-id="6c467-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-504">Boolean</span></span>|  
|<span data-ttu-id="6c467-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-505">TYPE</span></span>|<span data-ttu-id="6c467-506">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-506">Int32</span></span>|  
|<span data-ttu-id="6c467-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6c467-507">FILL_FACTOR</span></span>|<span data-ttu-id="6c467-508">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-508">Int32</span></span>|  
|<span data-ttu-id="6c467-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6c467-509">INITIAL_SIZE</span></span>|<span data-ttu-id="6c467-510">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-510">Int32</span></span>|  
|<span data-ttu-id="6c467-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="6c467-511">NULLS</span></span>|<span data-ttu-id="6c467-512">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-512">Int32</span></span>|  
|<span data-ttu-id="6c467-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6c467-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6c467-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-514">Boolean</span></span>|  
|<span data-ttu-id="6c467-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6c467-515">AUTO_UPDATE</span></span>|<span data-ttu-id="6c467-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-516">Boolean</span></span>|  
|<span data-ttu-id="6c467-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6c467-517">NULL_COLLATION</span></span>|<span data-ttu-id="6c467-518">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-518">Int32</span></span>|  
|<span data-ttu-id="6c467-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6c467-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="6c467-520">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-520">Int64</span></span>|  
|<span data-ttu-id="6c467-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-521">COLUMN_NAME</span></span>|<span data-ttu-id="6c467-522">String</span><span class="sxs-lookup"><span data-stu-id="6c467-522">String</span></span>|  
|<span data-ttu-id="6c467-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-523">COLUMN_GUID</span></span>|<span data-ttu-id="6c467-524">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-524">Guid</span></span>|  
|<span data-ttu-id="6c467-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6c467-525">COLUMN_PROPID</span></span>|<span data-ttu-id="6c467-526">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-526">Int64</span></span>|  
|<span data-ttu-id="6c467-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="6c467-527">COLLATION</span></span>|<span data-ttu-id="6c467-528">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-528">Int16</span></span>|  
|<span data-ttu-id="6c467-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="6c467-529">CARDINALITY</span></span>|<span data-ttu-id="6c467-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="6c467-530">Decimal</span></span>|  
|<span data-ttu-id="6c467-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="6c467-531">PAGES</span></span>|<span data-ttu-id="6c467-532">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-532">Int32</span></span>|  
|<span data-ttu-id="6c467-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6c467-533">FILTER_CONDITION</span></span>|<span data-ttu-id="6c467-534">String</span><span class="sxs-lookup"><span data-stu-id="6c467-534">String</span></span>|  
|<span data-ttu-id="6c467-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="6c467-535">INTEGRATED</span></span>|<span data-ttu-id="6c467-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="6c467-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="6c467-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="6c467-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="6c467-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="6c467-539">資料表</span><span class="sxs-lookup"><span data-stu-id="6c467-539">Tables</span></span>  
  
-   <span data-ttu-id="6c467-540">資料行</span><span class="sxs-lookup"><span data-stu-id="6c467-540">Columns</span></span>  
  
-   <span data-ttu-id="6c467-541">程序</span><span class="sxs-lookup"><span data-stu-id="6c467-541">Procedures</span></span>  
  
-   <span data-ttu-id="6c467-542">檢視</span><span class="sxs-lookup"><span data-stu-id="6c467-542">Views</span></span>  
  
-   <span data-ttu-id="6c467-543">Indexes</span><span class="sxs-lookup"><span data-stu-id="6c467-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6c467-544">資料表</span><span class="sxs-lookup"><span data-stu-id="6c467-544">Tables</span></span>  
  
|<span data-ttu-id="6c467-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-545">ColumnName</span></span>|<span data-ttu-id="6c467-546">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-547">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-548">String</span><span class="sxs-lookup"><span data-stu-id="6c467-548">String</span></span>|  
|<span data-ttu-id="6c467-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-550">String</span><span class="sxs-lookup"><span data-stu-id="6c467-550">String</span></span>|  
|<span data-ttu-id="6c467-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-551">TABLE_NAME</span></span>|<span data-ttu-id="6c467-552">String</span><span class="sxs-lookup"><span data-stu-id="6c467-552">String</span></span>|  
|<span data-ttu-id="6c467-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-553">TABLE_TYPE</span></span>|<span data-ttu-id="6c467-554">String</span><span class="sxs-lookup"><span data-stu-id="6c467-554">String</span></span>|  
|<span data-ttu-id="6c467-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-555">TABLE_GUID</span></span>|<span data-ttu-id="6c467-556">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-556">Guid</span></span>|  
|<span data-ttu-id="6c467-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-557">DESCRIPTION</span></span>|<span data-ttu-id="6c467-558">String</span><span class="sxs-lookup"><span data-stu-id="6c467-558">String</span></span>|  
|<span data-ttu-id="6c467-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6c467-559">TABLE_PROPID</span></span>|<span data-ttu-id="6c467-560">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-560">Int64</span></span>|  
|<span data-ttu-id="6c467-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6c467-561">DATE_CREATED</span></span>|<span data-ttu-id="6c467-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-562">DateTime</span></span>|  
|<span data-ttu-id="6c467-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6c467-563">DATE_MODIFIED</span></span>|<span data-ttu-id="6c467-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6c467-565">資料行</span><span class="sxs-lookup"><span data-stu-id="6c467-565">Columns</span></span>  
  
|<span data-ttu-id="6c467-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-566">ColumnName</span></span>|<span data-ttu-id="6c467-567">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-568">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-569">String</span><span class="sxs-lookup"><span data-stu-id="6c467-569">String</span></span>|  
|<span data-ttu-id="6c467-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-571">String</span><span class="sxs-lookup"><span data-stu-id="6c467-571">String</span></span>|  
|<span data-ttu-id="6c467-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-572">TABLE_NAME</span></span>|<span data-ttu-id="6c467-573">String</span><span class="sxs-lookup"><span data-stu-id="6c467-573">String</span></span>|  
|<span data-ttu-id="6c467-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-574">COLUMN_NAME</span></span>|<span data-ttu-id="6c467-575">String</span><span class="sxs-lookup"><span data-stu-id="6c467-575">String</span></span>|  
|<span data-ttu-id="6c467-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-576">COLUMN_GUID</span></span>|<span data-ttu-id="6c467-577">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-577">Guid</span></span>|  
|<span data-ttu-id="6c467-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6c467-578">COLUMN_PROPID</span></span>|<span data-ttu-id="6c467-579">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-579">Int64</span></span>|  
|<span data-ttu-id="6c467-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6c467-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="6c467-581">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-581">Int64</span></span>|  
|<span data-ttu-id="6c467-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6c467-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6c467-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-583">Boolean</span></span>|  
|<span data-ttu-id="6c467-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6c467-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6c467-585">String</span><span class="sxs-lookup"><span data-stu-id="6c467-585">String</span></span>|  
|<span data-ttu-id="6c467-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6c467-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="6c467-587">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-587">Int64</span></span>|  
|<span data-ttu-id="6c467-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6c467-588">IS_NULLABLE</span></span>|<span data-ttu-id="6c467-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-589">Boolean</span></span>|  
|<span data-ttu-id="6c467-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-590">DATA_TYPE</span></span>|<span data-ttu-id="6c467-591">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-591">Int32</span></span>|  
|<span data-ttu-id="6c467-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-592">TYPE_GUID</span></span>|<span data-ttu-id="6c467-593">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-593">Guid</span></span>|  
|<span data-ttu-id="6c467-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6c467-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6c467-595">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-595">Int64</span></span>|  
|<span data-ttu-id="6c467-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6c467-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6c467-597">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-597">Int64</span></span>|  
|<span data-ttu-id="6c467-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6c467-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6c467-599">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-599">Int32</span></span>|  
|<span data-ttu-id="6c467-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6c467-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="6c467-601">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-601">Int16</span></span>|  
|<span data-ttu-id="6c467-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6c467-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="6c467-603">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-603">Int64</span></span>|  
|<span data-ttu-id="6c467-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6c467-605">String</span><span class="sxs-lookup"><span data-stu-id="6c467-605">String</span></span>|  
|<span data-ttu-id="6c467-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6c467-607">String</span><span class="sxs-lookup"><span data-stu-id="6c467-607">String</span></span>|  
|<span data-ttu-id="6c467-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6c467-609">String</span><span class="sxs-lookup"><span data-stu-id="6c467-609">String</span></span>|  
|<span data-ttu-id="6c467-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="6c467-611">String</span><span class="sxs-lookup"><span data-stu-id="6c467-611">String</span></span>|  
|<span data-ttu-id="6c467-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6c467-613">String</span><span class="sxs-lookup"><span data-stu-id="6c467-613">String</span></span>|  
|<span data-ttu-id="6c467-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-614">COLLATION_NAME</span></span>|<span data-ttu-id="6c467-615">String</span><span class="sxs-lookup"><span data-stu-id="6c467-615">String</span></span>|  
|<span data-ttu-id="6c467-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6c467-617">String</span><span class="sxs-lookup"><span data-stu-id="6c467-617">String</span></span>|  
|<span data-ttu-id="6c467-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6c467-619">String</span><span class="sxs-lookup"><span data-stu-id="6c467-619">String</span></span>|  
|<span data-ttu-id="6c467-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-620">DOMAIN_NAME</span></span>|<span data-ttu-id="6c467-621">String</span><span class="sxs-lookup"><span data-stu-id="6c467-621">String</span></span>|  
|<span data-ttu-id="6c467-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-622">DESCRIPTION</span></span>|<span data-ttu-id="6c467-623">String</span><span class="sxs-lookup"><span data-stu-id="6c467-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6c467-624">程序</span><span class="sxs-lookup"><span data-stu-id="6c467-624">Procedures</span></span>  
  
|<span data-ttu-id="6c467-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-625">ColumnName</span></span>|<span data-ttu-id="6c467-626">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6c467-628">String</span><span class="sxs-lookup"><span data-stu-id="6c467-628">String</span></span>|  
|<span data-ttu-id="6c467-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6c467-630">String</span><span class="sxs-lookup"><span data-stu-id="6c467-630">String</span></span>|  
|<span data-ttu-id="6c467-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="6c467-632">String</span><span class="sxs-lookup"><span data-stu-id="6c467-632">String</span></span>|  
|<span data-ttu-id="6c467-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6c467-634">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-634">Int16</span></span>|  
|<span data-ttu-id="6c467-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6c467-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6c467-636">String</span><span class="sxs-lookup"><span data-stu-id="6c467-636">String</span></span>|  
|<span data-ttu-id="6c467-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-637">DESCRIPTION</span></span>|<span data-ttu-id="6c467-638">String</span><span class="sxs-lookup"><span data-stu-id="6c467-638">String</span></span>|  
|<span data-ttu-id="6c467-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6c467-639">DATE_CREATED</span></span>|<span data-ttu-id="6c467-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-640">DateTime</span></span>|  
|<span data-ttu-id="6c467-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6c467-641">DATE_MODIFIED</span></span>|<span data-ttu-id="6c467-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="6c467-643">檢視</span><span class="sxs-lookup"><span data-stu-id="6c467-643">Views</span></span>  
  
|<span data-ttu-id="6c467-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-644">ColumnName</span></span>|<span data-ttu-id="6c467-645">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-646">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-647">String</span><span class="sxs-lookup"><span data-stu-id="6c467-647">String</span></span>|  
|<span data-ttu-id="6c467-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-649">String</span><span class="sxs-lookup"><span data-stu-id="6c467-649">String</span></span>|  
|<span data-ttu-id="6c467-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-650">TABLE_NAME</span></span>|<span data-ttu-id="6c467-651">String</span><span class="sxs-lookup"><span data-stu-id="6c467-651">String</span></span>|  
|<span data-ttu-id="6c467-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6c467-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="6c467-653">String</span><span class="sxs-lookup"><span data-stu-id="6c467-653">String</span></span>|  
|<span data-ttu-id="6c467-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-654">CHECK_OPTION</span></span>|<span data-ttu-id="6c467-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-655">Boolean</span></span>|  
|<span data-ttu-id="6c467-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="6c467-656">IS_UPDATABLE</span></span>|<span data-ttu-id="6c467-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-657">Boolean</span></span>|  
|<span data-ttu-id="6c467-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c467-658">DESCRIPTION</span></span>|<span data-ttu-id="6c467-659">String</span><span class="sxs-lookup"><span data-stu-id="6c467-659">String</span></span>|  
|<span data-ttu-id="6c467-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6c467-660">DATE_CREATED</span></span>|<span data-ttu-id="6c467-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-661">DateTime</span></span>|  
|<span data-ttu-id="6c467-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6c467-662">DATE_MODIFIED</span></span>|<span data-ttu-id="6c467-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="6c467-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6c467-664">Indexes</span><span class="sxs-lookup"><span data-stu-id="6c467-664">Indexes</span></span>  
  
|<span data-ttu-id="6c467-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6c467-665">ColumnName</span></span>|<span data-ttu-id="6c467-666">DataType</span><span class="sxs-lookup"><span data-stu-id="6c467-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6c467-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-667">TABLE_CATALOG</span></span>|<span data-ttu-id="6c467-668">String</span><span class="sxs-lookup"><span data-stu-id="6c467-668">String</span></span>|  
|<span data-ttu-id="6c467-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="6c467-670">String</span><span class="sxs-lookup"><span data-stu-id="6c467-670">String</span></span>|  
|<span data-ttu-id="6c467-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-671">TABLE_NAME</span></span>|<span data-ttu-id="6c467-672">String</span><span class="sxs-lookup"><span data-stu-id="6c467-672">String</span></span>|  
|<span data-ttu-id="6c467-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6c467-673">INDEX_CATALOG</span></span>|<span data-ttu-id="6c467-674">String</span><span class="sxs-lookup"><span data-stu-id="6c467-674">String</span></span>|  
|<span data-ttu-id="6c467-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6c467-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="6c467-676">String</span><span class="sxs-lookup"><span data-stu-id="6c467-676">String</span></span>|  
|<span data-ttu-id="6c467-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-677">INDEX_NAME</span></span>|<span data-ttu-id="6c467-678">String</span><span class="sxs-lookup"><span data-stu-id="6c467-678">String</span></span>|  
|<span data-ttu-id="6c467-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6c467-679">PRIMARY_KEY</span></span>|<span data-ttu-id="6c467-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-680">Boolean</span></span>|  
|<span data-ttu-id="6c467-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="6c467-681">UNIQUE</span></span>|<span data-ttu-id="6c467-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-682">Boolean</span></span>|  
|<span data-ttu-id="6c467-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6c467-683">CLUSTERED</span></span>|<span data-ttu-id="6c467-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-684">Boolean</span></span>|  
|<span data-ttu-id="6c467-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="6c467-685">TYPE</span></span>|<span data-ttu-id="6c467-686">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-686">Int32</span></span>|  
|<span data-ttu-id="6c467-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6c467-687">FILL_FACTOR</span></span>|<span data-ttu-id="6c467-688">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-688">Int32</span></span>|  
|<span data-ttu-id="6c467-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6c467-689">INITIAL_SIZE</span></span>|<span data-ttu-id="6c467-690">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-690">Int32</span></span>|  
|<span data-ttu-id="6c467-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="6c467-691">NULLS</span></span>|<span data-ttu-id="6c467-692">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-692">Int32</span></span>|  
|<span data-ttu-id="6c467-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6c467-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6c467-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-694">Boolean</span></span>|  
|<span data-ttu-id="6c467-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6c467-695">AUTO_UPDATE</span></span>|<span data-ttu-id="6c467-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-696">Boolean</span></span>|  
|<span data-ttu-id="6c467-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6c467-697">NULL_COLLATION</span></span>|<span data-ttu-id="6c467-698">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-698">Int32</span></span>|  
|<span data-ttu-id="6c467-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6c467-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="6c467-700">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-700">Int64</span></span>|  
|<span data-ttu-id="6c467-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6c467-701">COLUMN_NAME</span></span>|<span data-ttu-id="6c467-702">String</span><span class="sxs-lookup"><span data-stu-id="6c467-702">String</span></span>|  
|<span data-ttu-id="6c467-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6c467-703">COLUMN_GUID</span></span>|<span data-ttu-id="6c467-704">Guid</span><span class="sxs-lookup"><span data-stu-id="6c467-704">Guid</span></span>|  
|<span data-ttu-id="6c467-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6c467-705">COLUMN_PROPID</span></span>|<span data-ttu-id="6c467-706">Int64</span><span class="sxs-lookup"><span data-stu-id="6c467-706">Int64</span></span>|  
|<span data-ttu-id="6c467-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="6c467-707">COLLATION</span></span>|<span data-ttu-id="6c467-708">Int16</span><span class="sxs-lookup"><span data-stu-id="6c467-708">Int16</span></span>|  
|<span data-ttu-id="6c467-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="6c467-709">CARDINALITY</span></span>|<span data-ttu-id="6c467-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="6c467-710">Decimal</span></span>|  
|<span data-ttu-id="6c467-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="6c467-711">PAGES</span></span>|<span data-ttu-id="6c467-712">Int32</span><span class="sxs-lookup"><span data-stu-id="6c467-712">Int32</span></span>|  
|<span data-ttu-id="6c467-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6c467-713">FILTER_CONDITION</span></span>|<span data-ttu-id="6c467-714">String</span><span class="sxs-lookup"><span data-stu-id="6c467-714">String</span></span>|  
|<span data-ttu-id="6c467-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="6c467-715">INTEGRATED</span></span>|<span data-ttu-id="6c467-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="6c467-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c467-717">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c467-717">See Also</span></span>  
 [<span data-ttu-id="6c467-718">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6c467-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
