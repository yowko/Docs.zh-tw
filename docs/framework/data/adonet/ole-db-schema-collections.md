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
ms.openlocfilehash: 9b88308c5dad69ed1ba6f48f525931e94f13ef1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="62f64-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="62f64-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="62f64-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="62f64-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="62f64-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="62f64-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="62f64-105">Microsoft SQL Server OLE DB 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="62f64-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="62f64-106">資料表</span><span class="sxs-lookup"><span data-stu-id="62f64-106">Tables</span></span>  
  
-   <span data-ttu-id="62f64-107">資料行</span><span class="sxs-lookup"><span data-stu-id="62f64-107">Columns</span></span>  
  
-   <span data-ttu-id="62f64-108">程序</span><span class="sxs-lookup"><span data-stu-id="62f64-108">Procedures</span></span>  
  
-   <span data-ttu-id="62f64-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="62f64-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="62f64-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="62f64-110">Catalog</span></span>  
  
-   <span data-ttu-id="62f64-111">Indexes</span><span class="sxs-lookup"><span data-stu-id="62f64-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="62f64-112">資料表</span><span class="sxs-lookup"><span data-stu-id="62f64-112">Tables</span></span>  
  
|<span data-ttu-id="62f64-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-113">ColumnName</span></span>|<span data-ttu-id="62f64-114">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-115">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-116">String</span><span class="sxs-lookup"><span data-stu-id="62f64-116">String</span></span>|  
|<span data-ttu-id="62f64-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-118">String</span><span class="sxs-lookup"><span data-stu-id="62f64-118">String</span></span>|  
|<span data-ttu-id="62f64-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-119">TABLE_NAME</span></span>|<span data-ttu-id="62f64-120">String</span><span class="sxs-lookup"><span data-stu-id="62f64-120">String</span></span>|  
|<span data-ttu-id="62f64-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-121">TABLE_TYPE</span></span>|<span data-ttu-id="62f64-122">String</span><span class="sxs-lookup"><span data-stu-id="62f64-122">String</span></span>|  
|<span data-ttu-id="62f64-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-123">TABLE_GUID</span></span>|<span data-ttu-id="62f64-124">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-124">Guid</span></span>|  
|<span data-ttu-id="62f64-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-125">DESCRIPTION</span></span>|<span data-ttu-id="62f64-126">String</span><span class="sxs-lookup"><span data-stu-id="62f64-126">String</span></span>|  
|<span data-ttu-id="62f64-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="62f64-127">TABLE_PROPID</span></span>|<span data-ttu-id="62f64-128">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-128">Int64</span></span>|  
|<span data-ttu-id="62f64-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62f64-129">DATE_CREATED</span></span>|<span data-ttu-id="62f64-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-130">DateTime</span></span>|  
|<span data-ttu-id="62f64-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62f64-131">DATE_MODIFIED</span></span>|<span data-ttu-id="62f64-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="62f64-133">資料行</span><span class="sxs-lookup"><span data-stu-id="62f64-133">Columns</span></span>  
  
|<span data-ttu-id="62f64-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-134">ColumnName</span></span>|<span data-ttu-id="62f64-135">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-136">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-137">String</span><span class="sxs-lookup"><span data-stu-id="62f64-137">String</span></span>|  
|<span data-ttu-id="62f64-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-139">String</span><span class="sxs-lookup"><span data-stu-id="62f64-139">String</span></span>|  
|<span data-ttu-id="62f64-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-140">TABLE_NAME</span></span>|<span data-ttu-id="62f64-141">String</span><span class="sxs-lookup"><span data-stu-id="62f64-141">String</span></span>|  
|<span data-ttu-id="62f64-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-142">COLUMN_NAME</span></span>|<span data-ttu-id="62f64-143">String</span><span class="sxs-lookup"><span data-stu-id="62f64-143">String</span></span>|  
|<span data-ttu-id="62f64-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-144">COLUMN_GUID</span></span>|<span data-ttu-id="62f64-145">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-145">Guid</span></span>|  
|<span data-ttu-id="62f64-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62f64-146">COLUMN_PROPID</span></span>|<span data-ttu-id="62f64-147">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-147">Int64</span></span>|  
|<span data-ttu-id="62f64-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62f64-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="62f64-149">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-149">Int64</span></span>|  
|<span data-ttu-id="62f64-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="62f64-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="62f64-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-151">Boolean</span></span>|  
|<span data-ttu-id="62f64-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="62f64-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="62f64-153">String</span><span class="sxs-lookup"><span data-stu-id="62f64-153">String</span></span>|  
|<span data-ttu-id="62f64-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="62f64-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="62f64-155">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-155">Int64</span></span>|  
|<span data-ttu-id="62f64-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="62f64-156">IS_NULLABLE</span></span>|<span data-ttu-id="62f64-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-157">Boolean</span></span>|  
|<span data-ttu-id="62f64-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-158">DATA_TYPE</span></span>|<span data-ttu-id="62f64-159">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-159">Int32</span></span>|  
|<span data-ttu-id="62f64-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-160">TYPE_GUID</span></span>|<span data-ttu-id="62f64-161">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-161">Guid</span></span>|  
|<span data-ttu-id="62f64-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62f64-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="62f64-163">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-163">Int64</span></span>|  
|<span data-ttu-id="62f64-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62f64-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="62f64-165">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-165">Int64</span></span>|  
|<span data-ttu-id="62f64-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62f64-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="62f64-167">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-167">Int32</span></span>|  
|<span data-ttu-id="62f64-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="62f64-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="62f64-169">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-169">Int16</span></span>|  
|<span data-ttu-id="62f64-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62f64-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="62f64-171">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-171">Int64</span></span>|  
|<span data-ttu-id="62f64-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="62f64-173">String</span><span class="sxs-lookup"><span data-stu-id="62f64-173">String</span></span>|  
|<span data-ttu-id="62f64-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="62f64-175">String</span><span class="sxs-lookup"><span data-stu-id="62f64-175">String</span></span>|  
|<span data-ttu-id="62f64-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="62f64-177">String</span><span class="sxs-lookup"><span data-stu-id="62f64-177">String</span></span>|  
|<span data-ttu-id="62f64-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="62f64-179">String</span><span class="sxs-lookup"><span data-stu-id="62f64-179">String</span></span>|  
|<span data-ttu-id="62f64-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="62f64-181">String</span><span class="sxs-lookup"><span data-stu-id="62f64-181">String</span></span>|  
|<span data-ttu-id="62f64-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-182">COLLATION_NAME</span></span>|<span data-ttu-id="62f64-183">String</span><span class="sxs-lookup"><span data-stu-id="62f64-183">String</span></span>|  
|<span data-ttu-id="62f64-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="62f64-185">String</span><span class="sxs-lookup"><span data-stu-id="62f64-185">String</span></span>|  
|<span data-ttu-id="62f64-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="62f64-187">String</span><span class="sxs-lookup"><span data-stu-id="62f64-187">String</span></span>|  
|<span data-ttu-id="62f64-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-188">DOMAIN_NAME</span></span>|<span data-ttu-id="62f64-189">String</span><span class="sxs-lookup"><span data-stu-id="62f64-189">String</span></span>|  
|<span data-ttu-id="62f64-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-190">DESCRIPTION</span></span>|<span data-ttu-id="62f64-191">String</span><span class="sxs-lookup"><span data-stu-id="62f64-191">String</span></span>|  
|<span data-ttu-id="62f64-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="62f64-192">COLUMN_LCID</span></span>|<span data-ttu-id="62f64-193">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-193">Int32</span></span>|  
|<span data-ttu-id="62f64-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="62f64-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="62f64-195">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-195">Int32</span></span>|  
|<span data-ttu-id="62f64-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="62f64-196">COLUMN_SORTID</span></span>|<span data-ttu-id="62f64-197">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-197">Int32</span></span>|  
|<span data-ttu-id="62f64-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="62f64-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="62f64-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="62f64-199">Byte[]</span></span>|  
|<span data-ttu-id="62f64-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="62f64-200">IS_COMPUTED</span></span>|<span data-ttu-id="62f64-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="62f64-202">程序</span><span class="sxs-lookup"><span data-stu-id="62f64-202">Procedures</span></span>  
  
|<span data-ttu-id="62f64-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-203">ColumnName</span></span>|<span data-ttu-id="62f64-204">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="62f64-206">String</span><span class="sxs-lookup"><span data-stu-id="62f64-206">String</span></span>|  
|<span data-ttu-id="62f64-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="62f64-208">String</span><span class="sxs-lookup"><span data-stu-id="62f64-208">String</span></span>|  
|<span data-ttu-id="62f64-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="62f64-210">String</span><span class="sxs-lookup"><span data-stu-id="62f64-210">String</span></span>|  
|<span data-ttu-id="62f64-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="62f64-212">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-212">Int16</span></span>|  
|<span data-ttu-id="62f64-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="62f64-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="62f64-214">String</span><span class="sxs-lookup"><span data-stu-id="62f64-214">String</span></span>|  
|<span data-ttu-id="62f64-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-215">DESCRIPTION</span></span>|<span data-ttu-id="62f64-216">String</span><span class="sxs-lookup"><span data-stu-id="62f64-216">String</span></span>|  
|<span data-ttu-id="62f64-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62f64-217">DATE_CREATED</span></span>|<span data-ttu-id="62f64-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-218">DateTime</span></span>|  
|<span data-ttu-id="62f64-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62f64-219">DATE_MODIFIED</span></span>|<span data-ttu-id="62f64-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="62f64-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="62f64-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="62f64-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-222">ColumnName</span></span>|<span data-ttu-id="62f64-223">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="62f64-225">String</span><span class="sxs-lookup"><span data-stu-id="62f64-225">String</span></span>|  
|<span data-ttu-id="62f64-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="62f64-227">String</span><span class="sxs-lookup"><span data-stu-id="62f64-227">String</span></span>|  
|<span data-ttu-id="62f64-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="62f64-229">String</span><span class="sxs-lookup"><span data-stu-id="62f64-229">String</span></span>|  
|<span data-ttu-id="62f64-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-230">PARAMETER_NAME</span></span>|<span data-ttu-id="62f64-231">String</span><span class="sxs-lookup"><span data-stu-id="62f64-231">String</span></span>|  
|<span data-ttu-id="62f64-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62f64-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="62f64-233">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-233">Int32</span></span>|  
|<span data-ttu-id="62f64-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="62f64-235">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-235">Int32</span></span>|  
|<span data-ttu-id="62f64-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="62f64-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="62f64-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-237">Boolean</span></span>|  
|<span data-ttu-id="62f64-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="62f64-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="62f64-239">String</span><span class="sxs-lookup"><span data-stu-id="62f64-239">String</span></span>|  
|<span data-ttu-id="62f64-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="62f64-240">IS_NULLABLE</span></span>|<span data-ttu-id="62f64-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-241">Boolean</span></span>|  
|<span data-ttu-id="62f64-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-242">DATA_TYPE</span></span>|<span data-ttu-id="62f64-243">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-243">Int32</span></span>|  
|<span data-ttu-id="62f64-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62f64-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="62f64-245">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-245">Int64</span></span>|  
|<span data-ttu-id="62f64-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62f64-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="62f64-247">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-247">Int64</span></span>|  
|<span data-ttu-id="62f64-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62f64-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="62f64-249">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-249">Int32</span></span>|  
|<span data-ttu-id="62f64-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="62f64-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="62f64-251">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-251">Int16</span></span>|  
|<span data-ttu-id="62f64-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-252">DESCRIPTION</span></span>|<span data-ttu-id="62f64-253">String</span><span class="sxs-lookup"><span data-stu-id="62f64-253">String</span></span>|  
|<span data-ttu-id="62f64-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-254">TYPE_NAME</span></span>|<span data-ttu-id="62f64-255">String</span><span class="sxs-lookup"><span data-stu-id="62f64-255">String</span></span>|  
|<span data-ttu-id="62f64-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="62f64-257">String</span><span class="sxs-lookup"><span data-stu-id="62f64-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="62f64-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="62f64-258">Catalog</span></span>  
  
|<span data-ttu-id="62f64-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-259">ColumnName</span></span>|<span data-ttu-id="62f64-260">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-261">CATALOG_NAME</span></span>|<span data-ttu-id="62f64-262">String</span><span class="sxs-lookup"><span data-stu-id="62f64-262">String</span></span>|  
|<span data-ttu-id="62f64-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-263">DESCRIPTION</span></span>|<span data-ttu-id="62f64-264">String</span><span class="sxs-lookup"><span data-stu-id="62f64-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="62f64-265">Indexes</span><span class="sxs-lookup"><span data-stu-id="62f64-265">Indexes</span></span>  
  
|<span data-ttu-id="62f64-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-266">ColumnName</span></span>|<span data-ttu-id="62f64-267">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-268">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-269">String</span><span class="sxs-lookup"><span data-stu-id="62f64-269">String</span></span>|  
|<span data-ttu-id="62f64-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-271">String</span><span class="sxs-lookup"><span data-stu-id="62f64-271">String</span></span>|  
|<span data-ttu-id="62f64-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-272">TABLE_NAME</span></span>|<span data-ttu-id="62f64-273">String</span><span class="sxs-lookup"><span data-stu-id="62f64-273">String</span></span>|  
|<span data-ttu-id="62f64-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-274">INDEX_CATALOG</span></span>|<span data-ttu-id="62f64-275">String</span><span class="sxs-lookup"><span data-stu-id="62f64-275">String</span></span>|  
|<span data-ttu-id="62f64-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="62f64-277">String</span><span class="sxs-lookup"><span data-stu-id="62f64-277">String</span></span>|  
|<span data-ttu-id="62f64-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-278">INDEX_NAME</span></span>|<span data-ttu-id="62f64-279">String</span><span class="sxs-lookup"><span data-stu-id="62f64-279">String</span></span>|  
|<span data-ttu-id="62f64-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="62f64-280">PRIMARY_KEY</span></span>|<span data-ttu-id="62f64-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-281">Boolean</span></span>|  
|<span data-ttu-id="62f64-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="62f64-282">UNIQUE</span></span>|<span data-ttu-id="62f64-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-283">Boolean</span></span>|  
|<span data-ttu-id="62f64-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="62f64-284">CLUSTERED</span></span>|<span data-ttu-id="62f64-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-285">Boolean</span></span>|  
|<span data-ttu-id="62f64-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-286">TYPE</span></span>|<span data-ttu-id="62f64-287">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-287">Int32</span></span>|  
|<span data-ttu-id="62f64-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="62f64-288">FILL_FACTOR</span></span>|<span data-ttu-id="62f64-289">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-289">Int32</span></span>|  
|<span data-ttu-id="62f64-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="62f64-290">INITIAL_SIZE</span></span>|<span data-ttu-id="62f64-291">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-291">Int32</span></span>|  
|<span data-ttu-id="62f64-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="62f64-292">NULLS</span></span>|<span data-ttu-id="62f64-293">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-293">Int32</span></span>|  
|<span data-ttu-id="62f64-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="62f64-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="62f64-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-295">Boolean</span></span>|  
|<span data-ttu-id="62f64-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="62f64-296">AUTO_UPDATE</span></span>|<span data-ttu-id="62f64-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-297">Boolean</span></span>|  
|<span data-ttu-id="62f64-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="62f64-298">NULL_COLLATION</span></span>|<span data-ttu-id="62f64-299">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-299">Int32</span></span>|  
|<span data-ttu-id="62f64-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62f64-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="62f64-301">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-301">Int64</span></span>|  
|<span data-ttu-id="62f64-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-302">COLUMN_NAME</span></span>|<span data-ttu-id="62f64-303">String</span><span class="sxs-lookup"><span data-stu-id="62f64-303">String</span></span>|  
|<span data-ttu-id="62f64-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-304">COLUMN_GUID</span></span>|<span data-ttu-id="62f64-305">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-305">Guid</span></span>|  
|<span data-ttu-id="62f64-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62f64-306">COLUMN_PROPID</span></span>|<span data-ttu-id="62f64-307">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-307">Int64</span></span>|  
|<span data-ttu-id="62f64-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="62f64-308">COLLATION</span></span>|<span data-ttu-id="62f64-309">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-309">Int16</span></span>|  
|<span data-ttu-id="62f64-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="62f64-310">CARDINALITY</span></span>|<span data-ttu-id="62f64-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="62f64-311">Decimal</span></span>|  
|<span data-ttu-id="62f64-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="62f64-312">PAGES</span></span>|<span data-ttu-id="62f64-313">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-313">Int32</span></span>|  
|<span data-ttu-id="62f64-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="62f64-314">FILTER_CONDITION</span></span>|<span data-ttu-id="62f64-315">String</span><span class="sxs-lookup"><span data-stu-id="62f64-315">String</span></span>|  
|<span data-ttu-id="62f64-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="62f64-316">INTEGRATED</span></span>|<span data-ttu-id="62f64-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="62f64-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="62f64-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="62f64-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="62f64-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="62f64-320">資料表</span><span class="sxs-lookup"><span data-stu-id="62f64-320">Tables</span></span>  
  
-   <span data-ttu-id="62f64-321">資料行</span><span class="sxs-lookup"><span data-stu-id="62f64-321">Columns</span></span>  
  
-   <span data-ttu-id="62f64-322">程序</span><span class="sxs-lookup"><span data-stu-id="62f64-322">Procedures</span></span>  
  
-   <span data-ttu-id="62f64-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="62f64-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="62f64-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="62f64-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="62f64-325">檢視</span><span class="sxs-lookup"><span data-stu-id="62f64-325">Views</span></span>  
  
-   <span data-ttu-id="62f64-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="62f64-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="62f64-327">資料表</span><span class="sxs-lookup"><span data-stu-id="62f64-327">Tables</span></span>  
  
|<span data-ttu-id="62f64-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-328">ColumnName</span></span>|<span data-ttu-id="62f64-329">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-330">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-331">String</span><span class="sxs-lookup"><span data-stu-id="62f64-331">String</span></span>|  
|<span data-ttu-id="62f64-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-333">String</span><span class="sxs-lookup"><span data-stu-id="62f64-333">String</span></span>|  
|<span data-ttu-id="62f64-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-334">TABLE_NAME</span></span>|<span data-ttu-id="62f64-335">String</span><span class="sxs-lookup"><span data-stu-id="62f64-335">String</span></span>|  
|<span data-ttu-id="62f64-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-336">TABLE_TYPE</span></span>|<span data-ttu-id="62f64-337">String</span><span class="sxs-lookup"><span data-stu-id="62f64-337">String</span></span>|  
|<span data-ttu-id="62f64-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-338">TABLE_GUID</span></span>|<span data-ttu-id="62f64-339">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-339">Guid</span></span>|  
|<span data-ttu-id="62f64-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-340">DESCRIPTION</span></span>|<span data-ttu-id="62f64-341">String</span><span class="sxs-lookup"><span data-stu-id="62f64-341">String</span></span>|  
|<span data-ttu-id="62f64-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="62f64-342">TABLE_PROPID</span></span>|<span data-ttu-id="62f64-343">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-343">Int64</span></span>|  
|<span data-ttu-id="62f64-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62f64-344">DATE_CREATED</span></span>|<span data-ttu-id="62f64-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-345">DateTime</span></span>|  
|<span data-ttu-id="62f64-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62f64-346">DATE_MODIFIED</span></span>|<span data-ttu-id="62f64-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="62f64-348">資料行</span><span class="sxs-lookup"><span data-stu-id="62f64-348">Columns</span></span>  
  
|<span data-ttu-id="62f64-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-349">ColumnName</span></span>|<span data-ttu-id="62f64-350">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-351">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-352">String</span><span class="sxs-lookup"><span data-stu-id="62f64-352">String</span></span>|  
|<span data-ttu-id="62f64-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-354">String</span><span class="sxs-lookup"><span data-stu-id="62f64-354">String</span></span>|  
|<span data-ttu-id="62f64-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-355">TABLE_NAME</span></span>|<span data-ttu-id="62f64-356">String</span><span class="sxs-lookup"><span data-stu-id="62f64-356">String</span></span>|  
|<span data-ttu-id="62f64-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-357">COLUMN_NAME</span></span>|<span data-ttu-id="62f64-358">String</span><span class="sxs-lookup"><span data-stu-id="62f64-358">String</span></span>|  
|<span data-ttu-id="62f64-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-359">COLUMN_GUID</span></span>|<span data-ttu-id="62f64-360">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-360">Guid</span></span>|  
|<span data-ttu-id="62f64-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62f64-361">COLUMN_PROPID</span></span>|<span data-ttu-id="62f64-362">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-362">Int64</span></span>|  
|<span data-ttu-id="62f64-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62f64-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="62f64-364">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-364">Int64</span></span>|  
|<span data-ttu-id="62f64-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="62f64-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="62f64-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-366">Boolean</span></span>|  
|<span data-ttu-id="62f64-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="62f64-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="62f64-368">String</span><span class="sxs-lookup"><span data-stu-id="62f64-368">String</span></span>|  
|<span data-ttu-id="62f64-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="62f64-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="62f64-370">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-370">Int64</span></span>|  
|<span data-ttu-id="62f64-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="62f64-371">IS_NULLABLE</span></span>|<span data-ttu-id="62f64-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-372">Boolean</span></span>|  
|<span data-ttu-id="62f64-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-373">DATA_TYPE</span></span>|<span data-ttu-id="62f64-374">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-374">Int32</span></span>|  
|<span data-ttu-id="62f64-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-375">TYPE_GUID</span></span>|<span data-ttu-id="62f64-376">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-376">Guid</span></span>|  
|<span data-ttu-id="62f64-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62f64-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="62f64-378">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-378">Int64</span></span>|  
|<span data-ttu-id="62f64-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62f64-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="62f64-380">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-380">Int64</span></span>|  
|<span data-ttu-id="62f64-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62f64-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="62f64-382">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-382">Int32</span></span>|  
|<span data-ttu-id="62f64-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="62f64-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="62f64-384">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-384">Int16</span></span>|  
|<span data-ttu-id="62f64-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62f64-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="62f64-386">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-386">Int64</span></span>|  
|<span data-ttu-id="62f64-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="62f64-388">String</span><span class="sxs-lookup"><span data-stu-id="62f64-388">String</span></span>|  
|<span data-ttu-id="62f64-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="62f64-390">String</span><span class="sxs-lookup"><span data-stu-id="62f64-390">String</span></span>|  
|<span data-ttu-id="62f64-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="62f64-392">String</span><span class="sxs-lookup"><span data-stu-id="62f64-392">String</span></span>|  
|<span data-ttu-id="62f64-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="62f64-394">String</span><span class="sxs-lookup"><span data-stu-id="62f64-394">String</span></span>|  
|<span data-ttu-id="62f64-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="62f64-396">String</span><span class="sxs-lookup"><span data-stu-id="62f64-396">String</span></span>|  
|<span data-ttu-id="62f64-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-397">COLLATION_NAME</span></span>|<span data-ttu-id="62f64-398">String</span><span class="sxs-lookup"><span data-stu-id="62f64-398">String</span></span>|  
|<span data-ttu-id="62f64-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="62f64-400">String</span><span class="sxs-lookup"><span data-stu-id="62f64-400">String</span></span>|  
|<span data-ttu-id="62f64-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="62f64-402">String</span><span class="sxs-lookup"><span data-stu-id="62f64-402">String</span></span>|  
|<span data-ttu-id="62f64-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-403">DOMAIN_NAME</span></span>|<span data-ttu-id="62f64-404">String</span><span class="sxs-lookup"><span data-stu-id="62f64-404">String</span></span>|  
|<span data-ttu-id="62f64-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-405">DESCRIPTION</span></span>|<span data-ttu-id="62f64-406">String</span><span class="sxs-lookup"><span data-stu-id="62f64-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="62f64-407">程序</span><span class="sxs-lookup"><span data-stu-id="62f64-407">Procedures</span></span>  
  
|<span data-ttu-id="62f64-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-408">ColumnName</span></span>|<span data-ttu-id="62f64-409">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="62f64-411">String</span><span class="sxs-lookup"><span data-stu-id="62f64-411">String</span></span>|  
|<span data-ttu-id="62f64-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="62f64-413">String</span><span class="sxs-lookup"><span data-stu-id="62f64-413">String</span></span>|  
|<span data-ttu-id="62f64-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="62f64-415">String</span><span class="sxs-lookup"><span data-stu-id="62f64-415">String</span></span>|  
|<span data-ttu-id="62f64-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="62f64-417">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-417">Int16</span></span>|  
|<span data-ttu-id="62f64-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="62f64-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="62f64-419">String</span><span class="sxs-lookup"><span data-stu-id="62f64-419">String</span></span>|  
|<span data-ttu-id="62f64-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-420">DESCRIPTION</span></span>|<span data-ttu-id="62f64-421">String</span><span class="sxs-lookup"><span data-stu-id="62f64-421">String</span></span>|  
|<span data-ttu-id="62f64-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62f64-422">DATE_CREATED</span></span>|<span data-ttu-id="62f64-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-423">DateTime</span></span>|  
|<span data-ttu-id="62f64-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62f64-424">DATE_MODIFIED</span></span>|<span data-ttu-id="62f64-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="62f64-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="62f64-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="62f64-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-427">ColumnName</span></span>|<span data-ttu-id="62f64-428">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="62f64-430">String</span><span class="sxs-lookup"><span data-stu-id="62f64-430">String</span></span>|  
|<span data-ttu-id="62f64-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="62f64-432">String</span><span class="sxs-lookup"><span data-stu-id="62f64-432">String</span></span>|  
|<span data-ttu-id="62f64-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="62f64-434">String</span><span class="sxs-lookup"><span data-stu-id="62f64-434">String</span></span>|  
|<span data-ttu-id="62f64-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-435">COLUMN_NAME</span></span>|<span data-ttu-id="62f64-436">String</span><span class="sxs-lookup"><span data-stu-id="62f64-436">String</span></span>|  
|<span data-ttu-id="62f64-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-437">COLUMN_GUID</span></span>|<span data-ttu-id="62f64-438">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-438">Guid</span></span>|  
|<span data-ttu-id="62f64-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62f64-439">COLUMN_PROPID</span></span>|<span data-ttu-id="62f64-440">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-440">Int64</span></span>|  
|<span data-ttu-id="62f64-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="62f64-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="62f64-442">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-442">Int64</span></span>|  
|<span data-ttu-id="62f64-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62f64-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="62f64-444">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-444">Int64</span></span>|  
|<span data-ttu-id="62f64-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="62f64-445">IS_NULLABLE</span></span>|<span data-ttu-id="62f64-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-446">Boolean</span></span>|  
|<span data-ttu-id="62f64-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-447">DATA_TYPE</span></span>|<span data-ttu-id="62f64-448">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-448">Int32</span></span>|  
|<span data-ttu-id="62f64-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-449">TYPE_GUID</span></span>|<span data-ttu-id="62f64-450">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-450">Guid</span></span>|  
|<span data-ttu-id="62f64-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62f64-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="62f64-452">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-452">Int64</span></span>|  
|<span data-ttu-id="62f64-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62f64-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="62f64-454">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-454">Int64</span></span>|  
|<span data-ttu-id="62f64-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62f64-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="62f64-456">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-456">Int32</span></span>|  
|<span data-ttu-id="62f64-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="62f64-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="62f64-458">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-458">Int16</span></span>|  
|<span data-ttu-id="62f64-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-459">DESCRIPTION</span></span>|<span data-ttu-id="62f64-460">String</span><span class="sxs-lookup"><span data-stu-id="62f64-460">String</span></span>|  
|<span data-ttu-id="62f64-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="62f64-461">OVERLOAD</span></span>|<span data-ttu-id="62f64-462">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="62f64-463">檢視</span><span class="sxs-lookup"><span data-stu-id="62f64-463">Views</span></span>  
  
|<span data-ttu-id="62f64-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-464">ColumnName</span></span>|<span data-ttu-id="62f64-465">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-466">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-467">String</span><span class="sxs-lookup"><span data-stu-id="62f64-467">String</span></span>|  
|<span data-ttu-id="62f64-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-469">String</span><span class="sxs-lookup"><span data-stu-id="62f64-469">String</span></span>|  
|<span data-ttu-id="62f64-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-470">TABLE_NAME</span></span>|<span data-ttu-id="62f64-471">String</span><span class="sxs-lookup"><span data-stu-id="62f64-471">String</span></span>|  
|<span data-ttu-id="62f64-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="62f64-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="62f64-473">String</span><span class="sxs-lookup"><span data-stu-id="62f64-473">String</span></span>|  
|<span data-ttu-id="62f64-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-474">CHECK_OPTION</span></span>|<span data-ttu-id="62f64-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-475">Boolean</span></span>|  
|<span data-ttu-id="62f64-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="62f64-476">IS_UPDATABLE</span></span>|<span data-ttu-id="62f64-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-477">Boolean</span></span>|  
|<span data-ttu-id="62f64-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-478">DESCRIPTION</span></span>|<span data-ttu-id="62f64-479">String</span><span class="sxs-lookup"><span data-stu-id="62f64-479">String</span></span>|  
|<span data-ttu-id="62f64-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62f64-480">DATE_CREATED</span></span>|<span data-ttu-id="62f64-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-481">DateTime</span></span>|  
|<span data-ttu-id="62f64-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62f64-482">DATE_MODIFIED</span></span>|<span data-ttu-id="62f64-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="62f64-484">Indexes</span><span class="sxs-lookup"><span data-stu-id="62f64-484">Indexes</span></span>  
  
|<span data-ttu-id="62f64-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-485">ColumnName</span></span>|<span data-ttu-id="62f64-486">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-487">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-488">String</span><span class="sxs-lookup"><span data-stu-id="62f64-488">String</span></span>|  
|<span data-ttu-id="62f64-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-490">String</span><span class="sxs-lookup"><span data-stu-id="62f64-490">String</span></span>|  
|<span data-ttu-id="62f64-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-491">TABLE_NAME</span></span>|<span data-ttu-id="62f64-492">String</span><span class="sxs-lookup"><span data-stu-id="62f64-492">String</span></span>|  
|<span data-ttu-id="62f64-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-493">INDEX_CATALOG</span></span>|<span data-ttu-id="62f64-494">String</span><span class="sxs-lookup"><span data-stu-id="62f64-494">String</span></span>|  
|<span data-ttu-id="62f64-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="62f64-496">String</span><span class="sxs-lookup"><span data-stu-id="62f64-496">String</span></span>|  
|<span data-ttu-id="62f64-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-497">INDEX_NAME</span></span>|<span data-ttu-id="62f64-498">String</span><span class="sxs-lookup"><span data-stu-id="62f64-498">String</span></span>|  
|<span data-ttu-id="62f64-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="62f64-499">PRIMARY_KEY</span></span>|<span data-ttu-id="62f64-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-500">Boolean</span></span>|  
|<span data-ttu-id="62f64-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="62f64-501">UNIQUE</span></span>|<span data-ttu-id="62f64-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-502">Boolean</span></span>|  
|<span data-ttu-id="62f64-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="62f64-503">CLUSTERED</span></span>|<span data-ttu-id="62f64-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-504">Boolean</span></span>|  
|<span data-ttu-id="62f64-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-505">TYPE</span></span>|<span data-ttu-id="62f64-506">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-506">Int32</span></span>|  
|<span data-ttu-id="62f64-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="62f64-507">FILL_FACTOR</span></span>|<span data-ttu-id="62f64-508">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-508">Int32</span></span>|  
|<span data-ttu-id="62f64-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="62f64-509">INITIAL_SIZE</span></span>|<span data-ttu-id="62f64-510">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-510">Int32</span></span>|  
|<span data-ttu-id="62f64-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="62f64-511">NULLS</span></span>|<span data-ttu-id="62f64-512">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-512">Int32</span></span>|  
|<span data-ttu-id="62f64-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="62f64-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="62f64-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-514">Boolean</span></span>|  
|<span data-ttu-id="62f64-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="62f64-515">AUTO_UPDATE</span></span>|<span data-ttu-id="62f64-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-516">Boolean</span></span>|  
|<span data-ttu-id="62f64-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="62f64-517">NULL_COLLATION</span></span>|<span data-ttu-id="62f64-518">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-518">Int32</span></span>|  
|<span data-ttu-id="62f64-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62f64-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="62f64-520">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-520">Int64</span></span>|  
|<span data-ttu-id="62f64-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-521">COLUMN_NAME</span></span>|<span data-ttu-id="62f64-522">String</span><span class="sxs-lookup"><span data-stu-id="62f64-522">String</span></span>|  
|<span data-ttu-id="62f64-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-523">COLUMN_GUID</span></span>|<span data-ttu-id="62f64-524">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-524">Guid</span></span>|  
|<span data-ttu-id="62f64-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62f64-525">COLUMN_PROPID</span></span>|<span data-ttu-id="62f64-526">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-526">Int64</span></span>|  
|<span data-ttu-id="62f64-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="62f64-527">COLLATION</span></span>|<span data-ttu-id="62f64-528">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-528">Int16</span></span>|  
|<span data-ttu-id="62f64-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="62f64-529">CARDINALITY</span></span>|<span data-ttu-id="62f64-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="62f64-530">Decimal</span></span>|  
|<span data-ttu-id="62f64-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="62f64-531">PAGES</span></span>|<span data-ttu-id="62f64-532">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-532">Int32</span></span>|  
|<span data-ttu-id="62f64-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="62f64-533">FILTER_CONDITION</span></span>|<span data-ttu-id="62f64-534">String</span><span class="sxs-lookup"><span data-stu-id="62f64-534">String</span></span>|  
|<span data-ttu-id="62f64-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="62f64-535">INTEGRATED</span></span>|<span data-ttu-id="62f64-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="62f64-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="62f64-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="62f64-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="62f64-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="62f64-539">資料表</span><span class="sxs-lookup"><span data-stu-id="62f64-539">Tables</span></span>  
  
-   <span data-ttu-id="62f64-540">資料行</span><span class="sxs-lookup"><span data-stu-id="62f64-540">Columns</span></span>  
  
-   <span data-ttu-id="62f64-541">程序</span><span class="sxs-lookup"><span data-stu-id="62f64-541">Procedures</span></span>  
  
-   <span data-ttu-id="62f64-542">檢視</span><span class="sxs-lookup"><span data-stu-id="62f64-542">Views</span></span>  
  
-   <span data-ttu-id="62f64-543">Indexes</span><span class="sxs-lookup"><span data-stu-id="62f64-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="62f64-544">資料表</span><span class="sxs-lookup"><span data-stu-id="62f64-544">Tables</span></span>  
  
|<span data-ttu-id="62f64-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-545">ColumnName</span></span>|<span data-ttu-id="62f64-546">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-547">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-548">String</span><span class="sxs-lookup"><span data-stu-id="62f64-548">String</span></span>|  
|<span data-ttu-id="62f64-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-550">String</span><span class="sxs-lookup"><span data-stu-id="62f64-550">String</span></span>|  
|<span data-ttu-id="62f64-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-551">TABLE_NAME</span></span>|<span data-ttu-id="62f64-552">String</span><span class="sxs-lookup"><span data-stu-id="62f64-552">String</span></span>|  
|<span data-ttu-id="62f64-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-553">TABLE_TYPE</span></span>|<span data-ttu-id="62f64-554">String</span><span class="sxs-lookup"><span data-stu-id="62f64-554">String</span></span>|  
|<span data-ttu-id="62f64-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-555">TABLE_GUID</span></span>|<span data-ttu-id="62f64-556">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-556">Guid</span></span>|  
|<span data-ttu-id="62f64-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-557">DESCRIPTION</span></span>|<span data-ttu-id="62f64-558">String</span><span class="sxs-lookup"><span data-stu-id="62f64-558">String</span></span>|  
|<span data-ttu-id="62f64-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="62f64-559">TABLE_PROPID</span></span>|<span data-ttu-id="62f64-560">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-560">Int64</span></span>|  
|<span data-ttu-id="62f64-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62f64-561">DATE_CREATED</span></span>|<span data-ttu-id="62f64-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-562">DateTime</span></span>|  
|<span data-ttu-id="62f64-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62f64-563">DATE_MODIFIED</span></span>|<span data-ttu-id="62f64-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="62f64-565">資料行</span><span class="sxs-lookup"><span data-stu-id="62f64-565">Columns</span></span>  
  
|<span data-ttu-id="62f64-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-566">ColumnName</span></span>|<span data-ttu-id="62f64-567">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-568">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-569">String</span><span class="sxs-lookup"><span data-stu-id="62f64-569">String</span></span>|  
|<span data-ttu-id="62f64-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-571">String</span><span class="sxs-lookup"><span data-stu-id="62f64-571">String</span></span>|  
|<span data-ttu-id="62f64-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-572">TABLE_NAME</span></span>|<span data-ttu-id="62f64-573">String</span><span class="sxs-lookup"><span data-stu-id="62f64-573">String</span></span>|  
|<span data-ttu-id="62f64-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-574">COLUMN_NAME</span></span>|<span data-ttu-id="62f64-575">String</span><span class="sxs-lookup"><span data-stu-id="62f64-575">String</span></span>|  
|<span data-ttu-id="62f64-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-576">COLUMN_GUID</span></span>|<span data-ttu-id="62f64-577">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-577">Guid</span></span>|  
|<span data-ttu-id="62f64-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62f64-578">COLUMN_PROPID</span></span>|<span data-ttu-id="62f64-579">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-579">Int64</span></span>|  
|<span data-ttu-id="62f64-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62f64-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="62f64-581">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-581">Int64</span></span>|  
|<span data-ttu-id="62f64-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="62f64-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="62f64-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-583">Boolean</span></span>|  
|<span data-ttu-id="62f64-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="62f64-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="62f64-585">String</span><span class="sxs-lookup"><span data-stu-id="62f64-585">String</span></span>|  
|<span data-ttu-id="62f64-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="62f64-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="62f64-587">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-587">Int64</span></span>|  
|<span data-ttu-id="62f64-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="62f64-588">IS_NULLABLE</span></span>|<span data-ttu-id="62f64-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-589">Boolean</span></span>|  
|<span data-ttu-id="62f64-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-590">DATA_TYPE</span></span>|<span data-ttu-id="62f64-591">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-591">Int32</span></span>|  
|<span data-ttu-id="62f64-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-592">TYPE_GUID</span></span>|<span data-ttu-id="62f64-593">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-593">Guid</span></span>|  
|<span data-ttu-id="62f64-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62f64-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="62f64-595">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-595">Int64</span></span>|  
|<span data-ttu-id="62f64-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62f64-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="62f64-597">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-597">Int64</span></span>|  
|<span data-ttu-id="62f64-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62f64-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="62f64-599">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-599">Int32</span></span>|  
|<span data-ttu-id="62f64-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="62f64-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="62f64-601">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-601">Int16</span></span>|  
|<span data-ttu-id="62f64-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62f64-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="62f64-603">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-603">Int64</span></span>|  
|<span data-ttu-id="62f64-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="62f64-605">String</span><span class="sxs-lookup"><span data-stu-id="62f64-605">String</span></span>|  
|<span data-ttu-id="62f64-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="62f64-607">String</span><span class="sxs-lookup"><span data-stu-id="62f64-607">String</span></span>|  
|<span data-ttu-id="62f64-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="62f64-609">String</span><span class="sxs-lookup"><span data-stu-id="62f64-609">String</span></span>|  
|<span data-ttu-id="62f64-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="62f64-611">String</span><span class="sxs-lookup"><span data-stu-id="62f64-611">String</span></span>|  
|<span data-ttu-id="62f64-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="62f64-613">String</span><span class="sxs-lookup"><span data-stu-id="62f64-613">String</span></span>|  
|<span data-ttu-id="62f64-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-614">COLLATION_NAME</span></span>|<span data-ttu-id="62f64-615">String</span><span class="sxs-lookup"><span data-stu-id="62f64-615">String</span></span>|  
|<span data-ttu-id="62f64-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="62f64-617">String</span><span class="sxs-lookup"><span data-stu-id="62f64-617">String</span></span>|  
|<span data-ttu-id="62f64-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="62f64-619">String</span><span class="sxs-lookup"><span data-stu-id="62f64-619">String</span></span>|  
|<span data-ttu-id="62f64-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-620">DOMAIN_NAME</span></span>|<span data-ttu-id="62f64-621">String</span><span class="sxs-lookup"><span data-stu-id="62f64-621">String</span></span>|  
|<span data-ttu-id="62f64-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-622">DESCRIPTION</span></span>|<span data-ttu-id="62f64-623">String</span><span class="sxs-lookup"><span data-stu-id="62f64-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="62f64-624">程序</span><span class="sxs-lookup"><span data-stu-id="62f64-624">Procedures</span></span>  
  
|<span data-ttu-id="62f64-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-625">ColumnName</span></span>|<span data-ttu-id="62f64-626">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="62f64-628">String</span><span class="sxs-lookup"><span data-stu-id="62f64-628">String</span></span>|  
|<span data-ttu-id="62f64-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="62f64-630">String</span><span class="sxs-lookup"><span data-stu-id="62f64-630">String</span></span>|  
|<span data-ttu-id="62f64-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="62f64-632">String</span><span class="sxs-lookup"><span data-stu-id="62f64-632">String</span></span>|  
|<span data-ttu-id="62f64-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="62f64-634">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-634">Int16</span></span>|  
|<span data-ttu-id="62f64-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="62f64-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="62f64-636">String</span><span class="sxs-lookup"><span data-stu-id="62f64-636">String</span></span>|  
|<span data-ttu-id="62f64-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-637">DESCRIPTION</span></span>|<span data-ttu-id="62f64-638">String</span><span class="sxs-lookup"><span data-stu-id="62f64-638">String</span></span>|  
|<span data-ttu-id="62f64-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62f64-639">DATE_CREATED</span></span>|<span data-ttu-id="62f64-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-640">DateTime</span></span>|  
|<span data-ttu-id="62f64-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62f64-641">DATE_MODIFIED</span></span>|<span data-ttu-id="62f64-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="62f64-643">檢視</span><span class="sxs-lookup"><span data-stu-id="62f64-643">Views</span></span>  
  
|<span data-ttu-id="62f64-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-644">ColumnName</span></span>|<span data-ttu-id="62f64-645">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-646">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-647">String</span><span class="sxs-lookup"><span data-stu-id="62f64-647">String</span></span>|  
|<span data-ttu-id="62f64-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-649">String</span><span class="sxs-lookup"><span data-stu-id="62f64-649">String</span></span>|  
|<span data-ttu-id="62f64-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-650">TABLE_NAME</span></span>|<span data-ttu-id="62f64-651">String</span><span class="sxs-lookup"><span data-stu-id="62f64-651">String</span></span>|  
|<span data-ttu-id="62f64-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="62f64-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="62f64-653">String</span><span class="sxs-lookup"><span data-stu-id="62f64-653">String</span></span>|  
|<span data-ttu-id="62f64-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-654">CHECK_OPTION</span></span>|<span data-ttu-id="62f64-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-655">Boolean</span></span>|  
|<span data-ttu-id="62f64-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="62f64-656">IS_UPDATABLE</span></span>|<span data-ttu-id="62f64-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-657">Boolean</span></span>|  
|<span data-ttu-id="62f64-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62f64-658">DESCRIPTION</span></span>|<span data-ttu-id="62f64-659">String</span><span class="sxs-lookup"><span data-stu-id="62f64-659">String</span></span>|  
|<span data-ttu-id="62f64-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62f64-660">DATE_CREATED</span></span>|<span data-ttu-id="62f64-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-661">DateTime</span></span>|  
|<span data-ttu-id="62f64-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62f64-662">DATE_MODIFIED</span></span>|<span data-ttu-id="62f64-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="62f64-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="62f64-664">Indexes</span><span class="sxs-lookup"><span data-stu-id="62f64-664">Indexes</span></span>  
  
|<span data-ttu-id="62f64-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62f64-665">ColumnName</span></span>|<span data-ttu-id="62f64-666">DataType</span><span class="sxs-lookup"><span data-stu-id="62f64-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62f64-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-667">TABLE_CATALOG</span></span>|<span data-ttu-id="62f64-668">String</span><span class="sxs-lookup"><span data-stu-id="62f64-668">String</span></span>|  
|<span data-ttu-id="62f64-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="62f64-670">String</span><span class="sxs-lookup"><span data-stu-id="62f64-670">String</span></span>|  
|<span data-ttu-id="62f64-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-671">TABLE_NAME</span></span>|<span data-ttu-id="62f64-672">String</span><span class="sxs-lookup"><span data-stu-id="62f64-672">String</span></span>|  
|<span data-ttu-id="62f64-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62f64-673">INDEX_CATALOG</span></span>|<span data-ttu-id="62f64-674">String</span><span class="sxs-lookup"><span data-stu-id="62f64-674">String</span></span>|  
|<span data-ttu-id="62f64-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62f64-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="62f64-676">String</span><span class="sxs-lookup"><span data-stu-id="62f64-676">String</span></span>|  
|<span data-ttu-id="62f64-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-677">INDEX_NAME</span></span>|<span data-ttu-id="62f64-678">String</span><span class="sxs-lookup"><span data-stu-id="62f64-678">String</span></span>|  
|<span data-ttu-id="62f64-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="62f64-679">PRIMARY_KEY</span></span>|<span data-ttu-id="62f64-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-680">Boolean</span></span>|  
|<span data-ttu-id="62f64-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="62f64-681">UNIQUE</span></span>|<span data-ttu-id="62f64-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-682">Boolean</span></span>|  
|<span data-ttu-id="62f64-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="62f64-683">CLUSTERED</span></span>|<span data-ttu-id="62f64-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-684">Boolean</span></span>|  
|<span data-ttu-id="62f64-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="62f64-685">TYPE</span></span>|<span data-ttu-id="62f64-686">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-686">Int32</span></span>|  
|<span data-ttu-id="62f64-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="62f64-687">FILL_FACTOR</span></span>|<span data-ttu-id="62f64-688">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-688">Int32</span></span>|  
|<span data-ttu-id="62f64-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="62f64-689">INITIAL_SIZE</span></span>|<span data-ttu-id="62f64-690">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-690">Int32</span></span>|  
|<span data-ttu-id="62f64-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="62f64-691">NULLS</span></span>|<span data-ttu-id="62f64-692">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-692">Int32</span></span>|  
|<span data-ttu-id="62f64-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="62f64-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="62f64-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-694">Boolean</span></span>|  
|<span data-ttu-id="62f64-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="62f64-695">AUTO_UPDATE</span></span>|<span data-ttu-id="62f64-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-696">Boolean</span></span>|  
|<span data-ttu-id="62f64-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="62f64-697">NULL_COLLATION</span></span>|<span data-ttu-id="62f64-698">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-698">Int32</span></span>|  
|<span data-ttu-id="62f64-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62f64-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="62f64-700">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-700">Int64</span></span>|  
|<span data-ttu-id="62f64-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62f64-701">COLUMN_NAME</span></span>|<span data-ttu-id="62f64-702">String</span><span class="sxs-lookup"><span data-stu-id="62f64-702">String</span></span>|  
|<span data-ttu-id="62f64-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62f64-703">COLUMN_GUID</span></span>|<span data-ttu-id="62f64-704">Guid</span><span class="sxs-lookup"><span data-stu-id="62f64-704">Guid</span></span>|  
|<span data-ttu-id="62f64-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62f64-705">COLUMN_PROPID</span></span>|<span data-ttu-id="62f64-706">Int64</span><span class="sxs-lookup"><span data-stu-id="62f64-706">Int64</span></span>|  
|<span data-ttu-id="62f64-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="62f64-707">COLLATION</span></span>|<span data-ttu-id="62f64-708">Int16</span><span class="sxs-lookup"><span data-stu-id="62f64-708">Int16</span></span>|  
|<span data-ttu-id="62f64-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="62f64-709">CARDINALITY</span></span>|<span data-ttu-id="62f64-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="62f64-710">Decimal</span></span>|  
|<span data-ttu-id="62f64-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="62f64-711">PAGES</span></span>|<span data-ttu-id="62f64-712">Int32</span><span class="sxs-lookup"><span data-stu-id="62f64-712">Int32</span></span>|  
|<span data-ttu-id="62f64-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="62f64-713">FILTER_CONDITION</span></span>|<span data-ttu-id="62f64-714">String</span><span class="sxs-lookup"><span data-stu-id="62f64-714">String</span></span>|  
|<span data-ttu-id="62f64-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="62f64-715">INTEGRATED</span></span>|<span data-ttu-id="62f64-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="62f64-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62f64-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62f64-717">See Also</span></span>  
 [<span data-ttu-id="62f64-718">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="62f64-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
