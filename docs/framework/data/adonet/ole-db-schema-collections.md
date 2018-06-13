---
title: OLE DB 結構描述集合
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: f1cb5e1fe967088b44fa4045dfe50c1c57d963eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766929"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="e3303-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e3303-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="e3303-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="e3303-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="e3303-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="e3303-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="e3303-105">Microsoft SQL Server OLE DB 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="e3303-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e3303-106">資料表</span><span class="sxs-lookup"><span data-stu-id="e3303-106">Tables</span></span>  
  
-   <span data-ttu-id="e3303-107">資料行</span><span class="sxs-lookup"><span data-stu-id="e3303-107">Columns</span></span>  
  
-   <span data-ttu-id="e3303-108">程序</span><span class="sxs-lookup"><span data-stu-id="e3303-108">Procedures</span></span>  
  
-   <span data-ttu-id="e3303-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e3303-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="e3303-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="e3303-110">Catalog</span></span>  
  
-   <span data-ttu-id="e3303-111">Indexes</span><span class="sxs-lookup"><span data-stu-id="e3303-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="e3303-112">資料表</span><span class="sxs-lookup"><span data-stu-id="e3303-112">Tables</span></span>  
  
|<span data-ttu-id="e3303-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-113">ColumnName</span></span>|<span data-ttu-id="e3303-114">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-115">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-116">String</span><span class="sxs-lookup"><span data-stu-id="e3303-116">String</span></span>|  
|<span data-ttu-id="e3303-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-118">String</span><span class="sxs-lookup"><span data-stu-id="e3303-118">String</span></span>|  
|<span data-ttu-id="e3303-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-119">TABLE_NAME</span></span>|<span data-ttu-id="e3303-120">String</span><span class="sxs-lookup"><span data-stu-id="e3303-120">String</span></span>|  
|<span data-ttu-id="e3303-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-121">TABLE_TYPE</span></span>|<span data-ttu-id="e3303-122">String</span><span class="sxs-lookup"><span data-stu-id="e3303-122">String</span></span>|  
|<span data-ttu-id="e3303-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-123">TABLE_GUID</span></span>|<span data-ttu-id="e3303-124">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-124">Guid</span></span>|  
|<span data-ttu-id="e3303-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-125">DESCRIPTION</span></span>|<span data-ttu-id="e3303-126">String</span><span class="sxs-lookup"><span data-stu-id="e3303-126">String</span></span>|  
|<span data-ttu-id="e3303-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="e3303-127">TABLE_PROPID</span></span>|<span data-ttu-id="e3303-128">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-128">Int64</span></span>|  
|<span data-ttu-id="e3303-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e3303-129">DATE_CREATED</span></span>|<span data-ttu-id="e3303-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-130">DateTime</span></span>|  
|<span data-ttu-id="e3303-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e3303-131">DATE_MODIFIED</span></span>|<span data-ttu-id="e3303-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e3303-133">資料行</span><span class="sxs-lookup"><span data-stu-id="e3303-133">Columns</span></span>  
  
|<span data-ttu-id="e3303-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-134">ColumnName</span></span>|<span data-ttu-id="e3303-135">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-136">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-137">String</span><span class="sxs-lookup"><span data-stu-id="e3303-137">String</span></span>|  
|<span data-ttu-id="e3303-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-139">String</span><span class="sxs-lookup"><span data-stu-id="e3303-139">String</span></span>|  
|<span data-ttu-id="e3303-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-140">TABLE_NAME</span></span>|<span data-ttu-id="e3303-141">String</span><span class="sxs-lookup"><span data-stu-id="e3303-141">String</span></span>|  
|<span data-ttu-id="e3303-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-142">COLUMN_NAME</span></span>|<span data-ttu-id="e3303-143">String</span><span class="sxs-lookup"><span data-stu-id="e3303-143">String</span></span>|  
|<span data-ttu-id="e3303-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-144">COLUMN_GUID</span></span>|<span data-ttu-id="e3303-145">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-145">Guid</span></span>|  
|<span data-ttu-id="e3303-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e3303-146">COLUMN_PROPID</span></span>|<span data-ttu-id="e3303-147">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-147">Int64</span></span>|  
|<span data-ttu-id="e3303-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3303-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3303-149">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-149">Int64</span></span>|  
|<span data-ttu-id="e3303-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3303-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="e3303-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-151">Boolean</span></span>|  
|<span data-ttu-id="e3303-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3303-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="e3303-153">String</span><span class="sxs-lookup"><span data-stu-id="e3303-153">String</span></span>|  
|<span data-ttu-id="e3303-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e3303-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="e3303-155">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-155">Int64</span></span>|  
|<span data-ttu-id="e3303-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e3303-156">IS_NULLABLE</span></span>|<span data-ttu-id="e3303-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-157">Boolean</span></span>|  
|<span data-ttu-id="e3303-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-158">DATA_TYPE</span></span>|<span data-ttu-id="e3303-159">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-159">Int32</span></span>|  
|<span data-ttu-id="e3303-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-160">TYPE_GUID</span></span>|<span data-ttu-id="e3303-161">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-161">Guid</span></span>|  
|<span data-ttu-id="e3303-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3303-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="e3303-163">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-163">Int64</span></span>|  
|<span data-ttu-id="e3303-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3303-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="e3303-165">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-165">Int64</span></span>|  
|<span data-ttu-id="e3303-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e3303-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="e3303-167">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-167">Int32</span></span>|  
|<span data-ttu-id="e3303-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="e3303-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="e3303-169">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-169">Int16</span></span>|  
|<span data-ttu-id="e3303-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e3303-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="e3303-171">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-171">Int64</span></span>|  
|<span data-ttu-id="e3303-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="e3303-173">String</span><span class="sxs-lookup"><span data-stu-id="e3303-173">String</span></span>|  
|<span data-ttu-id="e3303-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="e3303-175">String</span><span class="sxs-lookup"><span data-stu-id="e3303-175">String</span></span>|  
|<span data-ttu-id="e3303-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="e3303-177">String</span><span class="sxs-lookup"><span data-stu-id="e3303-177">String</span></span>|  
|<span data-ttu-id="e3303-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="e3303-179">String</span><span class="sxs-lookup"><span data-stu-id="e3303-179">String</span></span>|  
|<span data-ttu-id="e3303-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="e3303-181">String</span><span class="sxs-lookup"><span data-stu-id="e3303-181">String</span></span>|  
|<span data-ttu-id="e3303-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-182">COLLATION_NAME</span></span>|<span data-ttu-id="e3303-183">String</span><span class="sxs-lookup"><span data-stu-id="e3303-183">String</span></span>|  
|<span data-ttu-id="e3303-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="e3303-185">String</span><span class="sxs-lookup"><span data-stu-id="e3303-185">String</span></span>|  
|<span data-ttu-id="e3303-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="e3303-187">String</span><span class="sxs-lookup"><span data-stu-id="e3303-187">String</span></span>|  
|<span data-ttu-id="e3303-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-188">DOMAIN_NAME</span></span>|<span data-ttu-id="e3303-189">String</span><span class="sxs-lookup"><span data-stu-id="e3303-189">String</span></span>|  
|<span data-ttu-id="e3303-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-190">DESCRIPTION</span></span>|<span data-ttu-id="e3303-191">String</span><span class="sxs-lookup"><span data-stu-id="e3303-191">String</span></span>|  
|<span data-ttu-id="e3303-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="e3303-192">COLUMN_LCID</span></span>|<span data-ttu-id="e3303-193">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-193">Int32</span></span>|  
|<span data-ttu-id="e3303-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="e3303-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="e3303-195">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-195">Int32</span></span>|  
|<span data-ttu-id="e3303-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="e3303-196">COLUMN_SORTID</span></span>|<span data-ttu-id="e3303-197">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-197">Int32</span></span>|  
|<span data-ttu-id="e3303-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="e3303-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="e3303-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="e3303-199">Byte[]</span></span>|  
|<span data-ttu-id="e3303-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="e3303-200">IS_COMPUTED</span></span>|<span data-ttu-id="e3303-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e3303-202">程序</span><span class="sxs-lookup"><span data-stu-id="e3303-202">Procedures</span></span>  
  
|<span data-ttu-id="e3303-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-203">ColumnName</span></span>|<span data-ttu-id="e3303-204">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="e3303-206">String</span><span class="sxs-lookup"><span data-stu-id="e3303-206">String</span></span>|  
|<span data-ttu-id="e3303-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="e3303-208">String</span><span class="sxs-lookup"><span data-stu-id="e3303-208">String</span></span>|  
|<span data-ttu-id="e3303-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3303-210">String</span><span class="sxs-lookup"><span data-stu-id="e3303-210">String</span></span>|  
|<span data-ttu-id="e3303-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e3303-212">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-212">Int16</span></span>|  
|<span data-ttu-id="e3303-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e3303-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="e3303-214">String</span><span class="sxs-lookup"><span data-stu-id="e3303-214">String</span></span>|  
|<span data-ttu-id="e3303-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-215">DESCRIPTION</span></span>|<span data-ttu-id="e3303-216">String</span><span class="sxs-lookup"><span data-stu-id="e3303-216">String</span></span>|  
|<span data-ttu-id="e3303-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e3303-217">DATE_CREATED</span></span>|<span data-ttu-id="e3303-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-218">DateTime</span></span>|  
|<span data-ttu-id="e3303-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e3303-219">DATE_MODIFIED</span></span>|<span data-ttu-id="e3303-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e3303-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e3303-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e3303-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-222">ColumnName</span></span>|<span data-ttu-id="e3303-223">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="e3303-225">String</span><span class="sxs-lookup"><span data-stu-id="e3303-225">String</span></span>|  
|<span data-ttu-id="e3303-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="e3303-227">String</span><span class="sxs-lookup"><span data-stu-id="e3303-227">String</span></span>|  
|<span data-ttu-id="e3303-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3303-229">String</span><span class="sxs-lookup"><span data-stu-id="e3303-229">String</span></span>|  
|<span data-ttu-id="e3303-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-230">PARAMETER_NAME</span></span>|<span data-ttu-id="e3303-231">String</span><span class="sxs-lookup"><span data-stu-id="e3303-231">String</span></span>|  
|<span data-ttu-id="e3303-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3303-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3303-233">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-233">Int32</span></span>|  
|<span data-ttu-id="e3303-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="e3303-235">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-235">Int32</span></span>|  
|<span data-ttu-id="e3303-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3303-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="e3303-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-237">Boolean</span></span>|  
|<span data-ttu-id="e3303-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3303-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="e3303-239">String</span><span class="sxs-lookup"><span data-stu-id="e3303-239">String</span></span>|  
|<span data-ttu-id="e3303-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e3303-240">IS_NULLABLE</span></span>|<span data-ttu-id="e3303-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-241">Boolean</span></span>|  
|<span data-ttu-id="e3303-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-242">DATA_TYPE</span></span>|<span data-ttu-id="e3303-243">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-243">Int32</span></span>|  
|<span data-ttu-id="e3303-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3303-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="e3303-245">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-245">Int64</span></span>|  
|<span data-ttu-id="e3303-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3303-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="e3303-247">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-247">Int64</span></span>|  
|<span data-ttu-id="e3303-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e3303-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="e3303-249">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-249">Int32</span></span>|  
|<span data-ttu-id="e3303-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="e3303-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="e3303-251">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-251">Int16</span></span>|  
|<span data-ttu-id="e3303-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-252">DESCRIPTION</span></span>|<span data-ttu-id="e3303-253">String</span><span class="sxs-lookup"><span data-stu-id="e3303-253">String</span></span>|  
|<span data-ttu-id="e3303-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-254">TYPE_NAME</span></span>|<span data-ttu-id="e3303-255">String</span><span class="sxs-lookup"><span data-stu-id="e3303-255">String</span></span>|  
|<span data-ttu-id="e3303-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="e3303-257">String</span><span class="sxs-lookup"><span data-stu-id="e3303-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="e3303-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="e3303-258">Catalog</span></span>  
  
|<span data-ttu-id="e3303-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-259">ColumnName</span></span>|<span data-ttu-id="e3303-260">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-261">CATALOG_NAME</span></span>|<span data-ttu-id="e3303-262">String</span><span class="sxs-lookup"><span data-stu-id="e3303-262">String</span></span>|  
|<span data-ttu-id="e3303-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-263">DESCRIPTION</span></span>|<span data-ttu-id="e3303-264">String</span><span class="sxs-lookup"><span data-stu-id="e3303-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e3303-265">Indexes</span><span class="sxs-lookup"><span data-stu-id="e3303-265">Indexes</span></span>  
  
|<span data-ttu-id="e3303-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-266">ColumnName</span></span>|<span data-ttu-id="e3303-267">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-268">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-269">String</span><span class="sxs-lookup"><span data-stu-id="e3303-269">String</span></span>|  
|<span data-ttu-id="e3303-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-271">String</span><span class="sxs-lookup"><span data-stu-id="e3303-271">String</span></span>|  
|<span data-ttu-id="e3303-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-272">TABLE_NAME</span></span>|<span data-ttu-id="e3303-273">String</span><span class="sxs-lookup"><span data-stu-id="e3303-273">String</span></span>|  
|<span data-ttu-id="e3303-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-274">INDEX_CATALOG</span></span>|<span data-ttu-id="e3303-275">String</span><span class="sxs-lookup"><span data-stu-id="e3303-275">String</span></span>|  
|<span data-ttu-id="e3303-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="e3303-277">String</span><span class="sxs-lookup"><span data-stu-id="e3303-277">String</span></span>|  
|<span data-ttu-id="e3303-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-278">INDEX_NAME</span></span>|<span data-ttu-id="e3303-279">String</span><span class="sxs-lookup"><span data-stu-id="e3303-279">String</span></span>|  
|<span data-ttu-id="e3303-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="e3303-280">PRIMARY_KEY</span></span>|<span data-ttu-id="e3303-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-281">Boolean</span></span>|  
|<span data-ttu-id="e3303-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="e3303-282">UNIQUE</span></span>|<span data-ttu-id="e3303-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-283">Boolean</span></span>|  
|<span data-ttu-id="e3303-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="e3303-284">CLUSTERED</span></span>|<span data-ttu-id="e3303-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-285">Boolean</span></span>|  
|<span data-ttu-id="e3303-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-286">TYPE</span></span>|<span data-ttu-id="e3303-287">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-287">Int32</span></span>|  
|<span data-ttu-id="e3303-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="e3303-288">FILL_FACTOR</span></span>|<span data-ttu-id="e3303-289">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-289">Int32</span></span>|  
|<span data-ttu-id="e3303-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="e3303-290">INITIAL_SIZE</span></span>|<span data-ttu-id="e3303-291">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-291">Int32</span></span>|  
|<span data-ttu-id="e3303-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="e3303-292">NULLS</span></span>|<span data-ttu-id="e3303-293">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-293">Int32</span></span>|  
|<span data-ttu-id="e3303-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="e3303-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="e3303-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-295">Boolean</span></span>|  
|<span data-ttu-id="e3303-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="e3303-296">AUTO_UPDATE</span></span>|<span data-ttu-id="e3303-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-297">Boolean</span></span>|  
|<span data-ttu-id="e3303-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="e3303-298">NULL_COLLATION</span></span>|<span data-ttu-id="e3303-299">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-299">Int32</span></span>|  
|<span data-ttu-id="e3303-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3303-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3303-301">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-301">Int64</span></span>|  
|<span data-ttu-id="e3303-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-302">COLUMN_NAME</span></span>|<span data-ttu-id="e3303-303">String</span><span class="sxs-lookup"><span data-stu-id="e3303-303">String</span></span>|  
|<span data-ttu-id="e3303-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-304">COLUMN_GUID</span></span>|<span data-ttu-id="e3303-305">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-305">Guid</span></span>|  
|<span data-ttu-id="e3303-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e3303-306">COLUMN_PROPID</span></span>|<span data-ttu-id="e3303-307">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-307">Int64</span></span>|  
|<span data-ttu-id="e3303-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="e3303-308">COLLATION</span></span>|<span data-ttu-id="e3303-309">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-309">Int16</span></span>|  
|<span data-ttu-id="e3303-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="e3303-310">CARDINALITY</span></span>|<span data-ttu-id="e3303-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="e3303-311">Decimal</span></span>|  
|<span data-ttu-id="e3303-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="e3303-312">PAGES</span></span>|<span data-ttu-id="e3303-313">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-313">Int32</span></span>|  
|<span data-ttu-id="e3303-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="e3303-314">FILTER_CONDITION</span></span>|<span data-ttu-id="e3303-315">String</span><span class="sxs-lookup"><span data-stu-id="e3303-315">String</span></span>|  
|<span data-ttu-id="e3303-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="e3303-316">INTEGRATED</span></span>|<span data-ttu-id="e3303-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="e3303-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="e3303-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="e3303-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="e3303-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e3303-320">資料表</span><span class="sxs-lookup"><span data-stu-id="e3303-320">Tables</span></span>  
  
-   <span data-ttu-id="e3303-321">資料行</span><span class="sxs-lookup"><span data-stu-id="e3303-321">Columns</span></span>  
  
-   <span data-ttu-id="e3303-322">程序</span><span class="sxs-lookup"><span data-stu-id="e3303-322">Procedures</span></span>  
  
-   <span data-ttu-id="e3303-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e3303-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="e3303-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e3303-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="e3303-325">檢視</span><span class="sxs-lookup"><span data-stu-id="e3303-325">Views</span></span>  
  
-   <span data-ttu-id="e3303-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="e3303-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="e3303-327">資料表</span><span class="sxs-lookup"><span data-stu-id="e3303-327">Tables</span></span>  
  
|<span data-ttu-id="e3303-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-328">ColumnName</span></span>|<span data-ttu-id="e3303-329">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-330">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-331">String</span><span class="sxs-lookup"><span data-stu-id="e3303-331">String</span></span>|  
|<span data-ttu-id="e3303-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-333">String</span><span class="sxs-lookup"><span data-stu-id="e3303-333">String</span></span>|  
|<span data-ttu-id="e3303-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-334">TABLE_NAME</span></span>|<span data-ttu-id="e3303-335">String</span><span class="sxs-lookup"><span data-stu-id="e3303-335">String</span></span>|  
|<span data-ttu-id="e3303-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-336">TABLE_TYPE</span></span>|<span data-ttu-id="e3303-337">String</span><span class="sxs-lookup"><span data-stu-id="e3303-337">String</span></span>|  
|<span data-ttu-id="e3303-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-338">TABLE_GUID</span></span>|<span data-ttu-id="e3303-339">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-339">Guid</span></span>|  
|<span data-ttu-id="e3303-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-340">DESCRIPTION</span></span>|<span data-ttu-id="e3303-341">String</span><span class="sxs-lookup"><span data-stu-id="e3303-341">String</span></span>|  
|<span data-ttu-id="e3303-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="e3303-342">TABLE_PROPID</span></span>|<span data-ttu-id="e3303-343">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-343">Int64</span></span>|  
|<span data-ttu-id="e3303-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e3303-344">DATE_CREATED</span></span>|<span data-ttu-id="e3303-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-345">DateTime</span></span>|  
|<span data-ttu-id="e3303-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e3303-346">DATE_MODIFIED</span></span>|<span data-ttu-id="e3303-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e3303-348">資料行</span><span class="sxs-lookup"><span data-stu-id="e3303-348">Columns</span></span>  
  
|<span data-ttu-id="e3303-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-349">ColumnName</span></span>|<span data-ttu-id="e3303-350">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-351">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-352">String</span><span class="sxs-lookup"><span data-stu-id="e3303-352">String</span></span>|  
|<span data-ttu-id="e3303-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-354">String</span><span class="sxs-lookup"><span data-stu-id="e3303-354">String</span></span>|  
|<span data-ttu-id="e3303-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-355">TABLE_NAME</span></span>|<span data-ttu-id="e3303-356">String</span><span class="sxs-lookup"><span data-stu-id="e3303-356">String</span></span>|  
|<span data-ttu-id="e3303-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-357">COLUMN_NAME</span></span>|<span data-ttu-id="e3303-358">String</span><span class="sxs-lookup"><span data-stu-id="e3303-358">String</span></span>|  
|<span data-ttu-id="e3303-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-359">COLUMN_GUID</span></span>|<span data-ttu-id="e3303-360">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-360">Guid</span></span>|  
|<span data-ttu-id="e3303-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e3303-361">COLUMN_PROPID</span></span>|<span data-ttu-id="e3303-362">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-362">Int64</span></span>|  
|<span data-ttu-id="e3303-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3303-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3303-364">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-364">Int64</span></span>|  
|<span data-ttu-id="e3303-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3303-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="e3303-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-366">Boolean</span></span>|  
|<span data-ttu-id="e3303-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3303-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="e3303-368">String</span><span class="sxs-lookup"><span data-stu-id="e3303-368">String</span></span>|  
|<span data-ttu-id="e3303-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e3303-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="e3303-370">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-370">Int64</span></span>|  
|<span data-ttu-id="e3303-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e3303-371">IS_NULLABLE</span></span>|<span data-ttu-id="e3303-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-372">Boolean</span></span>|  
|<span data-ttu-id="e3303-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-373">DATA_TYPE</span></span>|<span data-ttu-id="e3303-374">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-374">Int32</span></span>|  
|<span data-ttu-id="e3303-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-375">TYPE_GUID</span></span>|<span data-ttu-id="e3303-376">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-376">Guid</span></span>|  
|<span data-ttu-id="e3303-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3303-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="e3303-378">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-378">Int64</span></span>|  
|<span data-ttu-id="e3303-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3303-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="e3303-380">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-380">Int64</span></span>|  
|<span data-ttu-id="e3303-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e3303-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="e3303-382">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-382">Int32</span></span>|  
|<span data-ttu-id="e3303-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="e3303-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="e3303-384">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-384">Int16</span></span>|  
|<span data-ttu-id="e3303-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e3303-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="e3303-386">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-386">Int64</span></span>|  
|<span data-ttu-id="e3303-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="e3303-388">String</span><span class="sxs-lookup"><span data-stu-id="e3303-388">String</span></span>|  
|<span data-ttu-id="e3303-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="e3303-390">String</span><span class="sxs-lookup"><span data-stu-id="e3303-390">String</span></span>|  
|<span data-ttu-id="e3303-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="e3303-392">String</span><span class="sxs-lookup"><span data-stu-id="e3303-392">String</span></span>|  
|<span data-ttu-id="e3303-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="e3303-394">String</span><span class="sxs-lookup"><span data-stu-id="e3303-394">String</span></span>|  
|<span data-ttu-id="e3303-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="e3303-396">String</span><span class="sxs-lookup"><span data-stu-id="e3303-396">String</span></span>|  
|<span data-ttu-id="e3303-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-397">COLLATION_NAME</span></span>|<span data-ttu-id="e3303-398">String</span><span class="sxs-lookup"><span data-stu-id="e3303-398">String</span></span>|  
|<span data-ttu-id="e3303-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="e3303-400">String</span><span class="sxs-lookup"><span data-stu-id="e3303-400">String</span></span>|  
|<span data-ttu-id="e3303-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="e3303-402">String</span><span class="sxs-lookup"><span data-stu-id="e3303-402">String</span></span>|  
|<span data-ttu-id="e3303-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-403">DOMAIN_NAME</span></span>|<span data-ttu-id="e3303-404">String</span><span class="sxs-lookup"><span data-stu-id="e3303-404">String</span></span>|  
|<span data-ttu-id="e3303-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-405">DESCRIPTION</span></span>|<span data-ttu-id="e3303-406">String</span><span class="sxs-lookup"><span data-stu-id="e3303-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e3303-407">程序</span><span class="sxs-lookup"><span data-stu-id="e3303-407">Procedures</span></span>  
  
|<span data-ttu-id="e3303-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-408">ColumnName</span></span>|<span data-ttu-id="e3303-409">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="e3303-411">String</span><span class="sxs-lookup"><span data-stu-id="e3303-411">String</span></span>|  
|<span data-ttu-id="e3303-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="e3303-413">String</span><span class="sxs-lookup"><span data-stu-id="e3303-413">String</span></span>|  
|<span data-ttu-id="e3303-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3303-415">String</span><span class="sxs-lookup"><span data-stu-id="e3303-415">String</span></span>|  
|<span data-ttu-id="e3303-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e3303-417">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-417">Int16</span></span>|  
|<span data-ttu-id="e3303-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e3303-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="e3303-419">String</span><span class="sxs-lookup"><span data-stu-id="e3303-419">String</span></span>|  
|<span data-ttu-id="e3303-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-420">DESCRIPTION</span></span>|<span data-ttu-id="e3303-421">String</span><span class="sxs-lookup"><span data-stu-id="e3303-421">String</span></span>|  
|<span data-ttu-id="e3303-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e3303-422">DATE_CREATED</span></span>|<span data-ttu-id="e3303-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-423">DateTime</span></span>|  
|<span data-ttu-id="e3303-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e3303-424">DATE_MODIFIED</span></span>|<span data-ttu-id="e3303-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="e3303-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e3303-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="e3303-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-427">ColumnName</span></span>|<span data-ttu-id="e3303-428">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="e3303-430">String</span><span class="sxs-lookup"><span data-stu-id="e3303-430">String</span></span>|  
|<span data-ttu-id="e3303-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="e3303-432">String</span><span class="sxs-lookup"><span data-stu-id="e3303-432">String</span></span>|  
|<span data-ttu-id="e3303-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3303-434">String</span><span class="sxs-lookup"><span data-stu-id="e3303-434">String</span></span>|  
|<span data-ttu-id="e3303-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-435">COLUMN_NAME</span></span>|<span data-ttu-id="e3303-436">String</span><span class="sxs-lookup"><span data-stu-id="e3303-436">String</span></span>|  
|<span data-ttu-id="e3303-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-437">COLUMN_GUID</span></span>|<span data-ttu-id="e3303-438">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-438">Guid</span></span>|  
|<span data-ttu-id="e3303-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e3303-439">COLUMN_PROPID</span></span>|<span data-ttu-id="e3303-440">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-440">Int64</span></span>|  
|<span data-ttu-id="e3303-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="e3303-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="e3303-442">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-442">Int64</span></span>|  
|<span data-ttu-id="e3303-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3303-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3303-444">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-444">Int64</span></span>|  
|<span data-ttu-id="e3303-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e3303-445">IS_NULLABLE</span></span>|<span data-ttu-id="e3303-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-446">Boolean</span></span>|  
|<span data-ttu-id="e3303-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-447">DATA_TYPE</span></span>|<span data-ttu-id="e3303-448">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-448">Int32</span></span>|  
|<span data-ttu-id="e3303-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-449">TYPE_GUID</span></span>|<span data-ttu-id="e3303-450">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-450">Guid</span></span>|  
|<span data-ttu-id="e3303-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3303-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="e3303-452">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-452">Int64</span></span>|  
|<span data-ttu-id="e3303-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3303-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="e3303-454">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-454">Int64</span></span>|  
|<span data-ttu-id="e3303-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e3303-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="e3303-456">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-456">Int32</span></span>|  
|<span data-ttu-id="e3303-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="e3303-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="e3303-458">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-458">Int16</span></span>|  
|<span data-ttu-id="e3303-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-459">DESCRIPTION</span></span>|<span data-ttu-id="e3303-460">String</span><span class="sxs-lookup"><span data-stu-id="e3303-460">String</span></span>|  
|<span data-ttu-id="e3303-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="e3303-461">OVERLOAD</span></span>|<span data-ttu-id="e3303-462">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="e3303-463">檢視</span><span class="sxs-lookup"><span data-stu-id="e3303-463">Views</span></span>  
  
|<span data-ttu-id="e3303-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-464">ColumnName</span></span>|<span data-ttu-id="e3303-465">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-466">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-467">String</span><span class="sxs-lookup"><span data-stu-id="e3303-467">String</span></span>|  
|<span data-ttu-id="e3303-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-469">String</span><span class="sxs-lookup"><span data-stu-id="e3303-469">String</span></span>|  
|<span data-ttu-id="e3303-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-470">TABLE_NAME</span></span>|<span data-ttu-id="e3303-471">String</span><span class="sxs-lookup"><span data-stu-id="e3303-471">String</span></span>|  
|<span data-ttu-id="e3303-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e3303-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="e3303-473">String</span><span class="sxs-lookup"><span data-stu-id="e3303-473">String</span></span>|  
|<span data-ttu-id="e3303-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-474">CHECK_OPTION</span></span>|<span data-ttu-id="e3303-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-475">Boolean</span></span>|  
|<span data-ttu-id="e3303-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="e3303-476">IS_UPDATABLE</span></span>|<span data-ttu-id="e3303-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-477">Boolean</span></span>|  
|<span data-ttu-id="e3303-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-478">DESCRIPTION</span></span>|<span data-ttu-id="e3303-479">String</span><span class="sxs-lookup"><span data-stu-id="e3303-479">String</span></span>|  
|<span data-ttu-id="e3303-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e3303-480">DATE_CREATED</span></span>|<span data-ttu-id="e3303-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-481">DateTime</span></span>|  
|<span data-ttu-id="e3303-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e3303-482">DATE_MODIFIED</span></span>|<span data-ttu-id="e3303-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e3303-484">Indexes</span><span class="sxs-lookup"><span data-stu-id="e3303-484">Indexes</span></span>  
  
|<span data-ttu-id="e3303-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-485">ColumnName</span></span>|<span data-ttu-id="e3303-486">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-487">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-488">String</span><span class="sxs-lookup"><span data-stu-id="e3303-488">String</span></span>|  
|<span data-ttu-id="e3303-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-490">String</span><span class="sxs-lookup"><span data-stu-id="e3303-490">String</span></span>|  
|<span data-ttu-id="e3303-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-491">TABLE_NAME</span></span>|<span data-ttu-id="e3303-492">String</span><span class="sxs-lookup"><span data-stu-id="e3303-492">String</span></span>|  
|<span data-ttu-id="e3303-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-493">INDEX_CATALOG</span></span>|<span data-ttu-id="e3303-494">String</span><span class="sxs-lookup"><span data-stu-id="e3303-494">String</span></span>|  
|<span data-ttu-id="e3303-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="e3303-496">String</span><span class="sxs-lookup"><span data-stu-id="e3303-496">String</span></span>|  
|<span data-ttu-id="e3303-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-497">INDEX_NAME</span></span>|<span data-ttu-id="e3303-498">String</span><span class="sxs-lookup"><span data-stu-id="e3303-498">String</span></span>|  
|<span data-ttu-id="e3303-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="e3303-499">PRIMARY_KEY</span></span>|<span data-ttu-id="e3303-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-500">Boolean</span></span>|  
|<span data-ttu-id="e3303-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="e3303-501">UNIQUE</span></span>|<span data-ttu-id="e3303-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-502">Boolean</span></span>|  
|<span data-ttu-id="e3303-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="e3303-503">CLUSTERED</span></span>|<span data-ttu-id="e3303-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-504">Boolean</span></span>|  
|<span data-ttu-id="e3303-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-505">TYPE</span></span>|<span data-ttu-id="e3303-506">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-506">Int32</span></span>|  
|<span data-ttu-id="e3303-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="e3303-507">FILL_FACTOR</span></span>|<span data-ttu-id="e3303-508">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-508">Int32</span></span>|  
|<span data-ttu-id="e3303-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="e3303-509">INITIAL_SIZE</span></span>|<span data-ttu-id="e3303-510">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-510">Int32</span></span>|  
|<span data-ttu-id="e3303-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="e3303-511">NULLS</span></span>|<span data-ttu-id="e3303-512">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-512">Int32</span></span>|  
|<span data-ttu-id="e3303-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="e3303-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="e3303-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-514">Boolean</span></span>|  
|<span data-ttu-id="e3303-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="e3303-515">AUTO_UPDATE</span></span>|<span data-ttu-id="e3303-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-516">Boolean</span></span>|  
|<span data-ttu-id="e3303-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="e3303-517">NULL_COLLATION</span></span>|<span data-ttu-id="e3303-518">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-518">Int32</span></span>|  
|<span data-ttu-id="e3303-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3303-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3303-520">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-520">Int64</span></span>|  
|<span data-ttu-id="e3303-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-521">COLUMN_NAME</span></span>|<span data-ttu-id="e3303-522">String</span><span class="sxs-lookup"><span data-stu-id="e3303-522">String</span></span>|  
|<span data-ttu-id="e3303-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-523">COLUMN_GUID</span></span>|<span data-ttu-id="e3303-524">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-524">Guid</span></span>|  
|<span data-ttu-id="e3303-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e3303-525">COLUMN_PROPID</span></span>|<span data-ttu-id="e3303-526">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-526">Int64</span></span>|  
|<span data-ttu-id="e3303-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="e3303-527">COLLATION</span></span>|<span data-ttu-id="e3303-528">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-528">Int16</span></span>|  
|<span data-ttu-id="e3303-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="e3303-529">CARDINALITY</span></span>|<span data-ttu-id="e3303-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="e3303-530">Decimal</span></span>|  
|<span data-ttu-id="e3303-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="e3303-531">PAGES</span></span>|<span data-ttu-id="e3303-532">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-532">Int32</span></span>|  
|<span data-ttu-id="e3303-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="e3303-533">FILTER_CONDITION</span></span>|<span data-ttu-id="e3303-534">String</span><span class="sxs-lookup"><span data-stu-id="e3303-534">String</span></span>|  
|<span data-ttu-id="e3303-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="e3303-535">INTEGRATED</span></span>|<span data-ttu-id="e3303-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="e3303-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="e3303-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="e3303-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="e3303-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e3303-539">資料表</span><span class="sxs-lookup"><span data-stu-id="e3303-539">Tables</span></span>  
  
-   <span data-ttu-id="e3303-540">資料行</span><span class="sxs-lookup"><span data-stu-id="e3303-540">Columns</span></span>  
  
-   <span data-ttu-id="e3303-541">程序</span><span class="sxs-lookup"><span data-stu-id="e3303-541">Procedures</span></span>  
  
-   <span data-ttu-id="e3303-542">檢視</span><span class="sxs-lookup"><span data-stu-id="e3303-542">Views</span></span>  
  
-   <span data-ttu-id="e3303-543">Indexes</span><span class="sxs-lookup"><span data-stu-id="e3303-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="e3303-544">資料表</span><span class="sxs-lookup"><span data-stu-id="e3303-544">Tables</span></span>  
  
|<span data-ttu-id="e3303-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-545">ColumnName</span></span>|<span data-ttu-id="e3303-546">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-547">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-548">String</span><span class="sxs-lookup"><span data-stu-id="e3303-548">String</span></span>|  
|<span data-ttu-id="e3303-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-550">String</span><span class="sxs-lookup"><span data-stu-id="e3303-550">String</span></span>|  
|<span data-ttu-id="e3303-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-551">TABLE_NAME</span></span>|<span data-ttu-id="e3303-552">String</span><span class="sxs-lookup"><span data-stu-id="e3303-552">String</span></span>|  
|<span data-ttu-id="e3303-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-553">TABLE_TYPE</span></span>|<span data-ttu-id="e3303-554">String</span><span class="sxs-lookup"><span data-stu-id="e3303-554">String</span></span>|  
|<span data-ttu-id="e3303-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-555">TABLE_GUID</span></span>|<span data-ttu-id="e3303-556">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-556">Guid</span></span>|  
|<span data-ttu-id="e3303-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-557">DESCRIPTION</span></span>|<span data-ttu-id="e3303-558">String</span><span class="sxs-lookup"><span data-stu-id="e3303-558">String</span></span>|  
|<span data-ttu-id="e3303-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="e3303-559">TABLE_PROPID</span></span>|<span data-ttu-id="e3303-560">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-560">Int64</span></span>|  
|<span data-ttu-id="e3303-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e3303-561">DATE_CREATED</span></span>|<span data-ttu-id="e3303-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-562">DateTime</span></span>|  
|<span data-ttu-id="e3303-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e3303-563">DATE_MODIFIED</span></span>|<span data-ttu-id="e3303-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e3303-565">資料行</span><span class="sxs-lookup"><span data-stu-id="e3303-565">Columns</span></span>  
  
|<span data-ttu-id="e3303-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-566">ColumnName</span></span>|<span data-ttu-id="e3303-567">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-568">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-569">String</span><span class="sxs-lookup"><span data-stu-id="e3303-569">String</span></span>|  
|<span data-ttu-id="e3303-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-571">String</span><span class="sxs-lookup"><span data-stu-id="e3303-571">String</span></span>|  
|<span data-ttu-id="e3303-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-572">TABLE_NAME</span></span>|<span data-ttu-id="e3303-573">String</span><span class="sxs-lookup"><span data-stu-id="e3303-573">String</span></span>|  
|<span data-ttu-id="e3303-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-574">COLUMN_NAME</span></span>|<span data-ttu-id="e3303-575">String</span><span class="sxs-lookup"><span data-stu-id="e3303-575">String</span></span>|  
|<span data-ttu-id="e3303-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-576">COLUMN_GUID</span></span>|<span data-ttu-id="e3303-577">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-577">Guid</span></span>|  
|<span data-ttu-id="e3303-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e3303-578">COLUMN_PROPID</span></span>|<span data-ttu-id="e3303-579">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-579">Int64</span></span>|  
|<span data-ttu-id="e3303-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3303-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3303-581">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-581">Int64</span></span>|  
|<span data-ttu-id="e3303-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3303-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="e3303-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-583">Boolean</span></span>|  
|<span data-ttu-id="e3303-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3303-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="e3303-585">String</span><span class="sxs-lookup"><span data-stu-id="e3303-585">String</span></span>|  
|<span data-ttu-id="e3303-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e3303-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="e3303-587">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-587">Int64</span></span>|  
|<span data-ttu-id="e3303-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e3303-588">IS_NULLABLE</span></span>|<span data-ttu-id="e3303-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-589">Boolean</span></span>|  
|<span data-ttu-id="e3303-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-590">DATA_TYPE</span></span>|<span data-ttu-id="e3303-591">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-591">Int32</span></span>|  
|<span data-ttu-id="e3303-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-592">TYPE_GUID</span></span>|<span data-ttu-id="e3303-593">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-593">Guid</span></span>|  
|<span data-ttu-id="e3303-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3303-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="e3303-595">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-595">Int64</span></span>|  
|<span data-ttu-id="e3303-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e3303-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="e3303-597">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-597">Int64</span></span>|  
|<span data-ttu-id="e3303-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e3303-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="e3303-599">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-599">Int32</span></span>|  
|<span data-ttu-id="e3303-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="e3303-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="e3303-601">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-601">Int16</span></span>|  
|<span data-ttu-id="e3303-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e3303-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="e3303-603">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-603">Int64</span></span>|  
|<span data-ttu-id="e3303-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="e3303-605">String</span><span class="sxs-lookup"><span data-stu-id="e3303-605">String</span></span>|  
|<span data-ttu-id="e3303-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="e3303-607">String</span><span class="sxs-lookup"><span data-stu-id="e3303-607">String</span></span>|  
|<span data-ttu-id="e3303-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="e3303-609">String</span><span class="sxs-lookup"><span data-stu-id="e3303-609">String</span></span>|  
|<span data-ttu-id="e3303-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="e3303-611">String</span><span class="sxs-lookup"><span data-stu-id="e3303-611">String</span></span>|  
|<span data-ttu-id="e3303-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="e3303-613">String</span><span class="sxs-lookup"><span data-stu-id="e3303-613">String</span></span>|  
|<span data-ttu-id="e3303-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-614">COLLATION_NAME</span></span>|<span data-ttu-id="e3303-615">String</span><span class="sxs-lookup"><span data-stu-id="e3303-615">String</span></span>|  
|<span data-ttu-id="e3303-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="e3303-617">String</span><span class="sxs-lookup"><span data-stu-id="e3303-617">String</span></span>|  
|<span data-ttu-id="e3303-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="e3303-619">String</span><span class="sxs-lookup"><span data-stu-id="e3303-619">String</span></span>|  
|<span data-ttu-id="e3303-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-620">DOMAIN_NAME</span></span>|<span data-ttu-id="e3303-621">String</span><span class="sxs-lookup"><span data-stu-id="e3303-621">String</span></span>|  
|<span data-ttu-id="e3303-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-622">DESCRIPTION</span></span>|<span data-ttu-id="e3303-623">String</span><span class="sxs-lookup"><span data-stu-id="e3303-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e3303-624">程序</span><span class="sxs-lookup"><span data-stu-id="e3303-624">Procedures</span></span>  
  
|<span data-ttu-id="e3303-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-625">ColumnName</span></span>|<span data-ttu-id="e3303-626">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="e3303-628">String</span><span class="sxs-lookup"><span data-stu-id="e3303-628">String</span></span>|  
|<span data-ttu-id="e3303-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="e3303-630">String</span><span class="sxs-lookup"><span data-stu-id="e3303-630">String</span></span>|  
|<span data-ttu-id="e3303-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="e3303-632">String</span><span class="sxs-lookup"><span data-stu-id="e3303-632">String</span></span>|  
|<span data-ttu-id="e3303-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e3303-634">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-634">Int16</span></span>|  
|<span data-ttu-id="e3303-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e3303-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="e3303-636">String</span><span class="sxs-lookup"><span data-stu-id="e3303-636">String</span></span>|  
|<span data-ttu-id="e3303-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-637">DESCRIPTION</span></span>|<span data-ttu-id="e3303-638">String</span><span class="sxs-lookup"><span data-stu-id="e3303-638">String</span></span>|  
|<span data-ttu-id="e3303-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e3303-639">DATE_CREATED</span></span>|<span data-ttu-id="e3303-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-640">DateTime</span></span>|  
|<span data-ttu-id="e3303-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e3303-641">DATE_MODIFIED</span></span>|<span data-ttu-id="e3303-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="e3303-643">檢視</span><span class="sxs-lookup"><span data-stu-id="e3303-643">Views</span></span>  
  
|<span data-ttu-id="e3303-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-644">ColumnName</span></span>|<span data-ttu-id="e3303-645">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-646">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-647">String</span><span class="sxs-lookup"><span data-stu-id="e3303-647">String</span></span>|  
|<span data-ttu-id="e3303-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-649">String</span><span class="sxs-lookup"><span data-stu-id="e3303-649">String</span></span>|  
|<span data-ttu-id="e3303-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-650">TABLE_NAME</span></span>|<span data-ttu-id="e3303-651">String</span><span class="sxs-lookup"><span data-stu-id="e3303-651">String</span></span>|  
|<span data-ttu-id="e3303-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e3303-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="e3303-653">String</span><span class="sxs-lookup"><span data-stu-id="e3303-653">String</span></span>|  
|<span data-ttu-id="e3303-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-654">CHECK_OPTION</span></span>|<span data-ttu-id="e3303-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-655">Boolean</span></span>|  
|<span data-ttu-id="e3303-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="e3303-656">IS_UPDATABLE</span></span>|<span data-ttu-id="e3303-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-657">Boolean</span></span>|  
|<span data-ttu-id="e3303-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3303-658">DESCRIPTION</span></span>|<span data-ttu-id="e3303-659">String</span><span class="sxs-lookup"><span data-stu-id="e3303-659">String</span></span>|  
|<span data-ttu-id="e3303-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e3303-660">DATE_CREATED</span></span>|<span data-ttu-id="e3303-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-661">DateTime</span></span>|  
|<span data-ttu-id="e3303-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e3303-662">DATE_MODIFIED</span></span>|<span data-ttu-id="e3303-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="e3303-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e3303-664">Indexes</span><span class="sxs-lookup"><span data-stu-id="e3303-664">Indexes</span></span>  
  
|<span data-ttu-id="e3303-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e3303-665">ColumnName</span></span>|<span data-ttu-id="e3303-666">DataType</span><span class="sxs-lookup"><span data-stu-id="e3303-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e3303-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-667">TABLE_CATALOG</span></span>|<span data-ttu-id="e3303-668">String</span><span class="sxs-lookup"><span data-stu-id="e3303-668">String</span></span>|  
|<span data-ttu-id="e3303-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="e3303-670">String</span><span class="sxs-lookup"><span data-stu-id="e3303-670">String</span></span>|  
|<span data-ttu-id="e3303-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-671">TABLE_NAME</span></span>|<span data-ttu-id="e3303-672">String</span><span class="sxs-lookup"><span data-stu-id="e3303-672">String</span></span>|  
|<span data-ttu-id="e3303-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e3303-673">INDEX_CATALOG</span></span>|<span data-ttu-id="e3303-674">String</span><span class="sxs-lookup"><span data-stu-id="e3303-674">String</span></span>|  
|<span data-ttu-id="e3303-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e3303-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="e3303-676">String</span><span class="sxs-lookup"><span data-stu-id="e3303-676">String</span></span>|  
|<span data-ttu-id="e3303-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-677">INDEX_NAME</span></span>|<span data-ttu-id="e3303-678">String</span><span class="sxs-lookup"><span data-stu-id="e3303-678">String</span></span>|  
|<span data-ttu-id="e3303-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="e3303-679">PRIMARY_KEY</span></span>|<span data-ttu-id="e3303-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-680">Boolean</span></span>|  
|<span data-ttu-id="e3303-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="e3303-681">UNIQUE</span></span>|<span data-ttu-id="e3303-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-682">Boolean</span></span>|  
|<span data-ttu-id="e3303-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="e3303-683">CLUSTERED</span></span>|<span data-ttu-id="e3303-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-684">Boolean</span></span>|  
|<span data-ttu-id="e3303-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="e3303-685">TYPE</span></span>|<span data-ttu-id="e3303-686">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-686">Int32</span></span>|  
|<span data-ttu-id="e3303-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="e3303-687">FILL_FACTOR</span></span>|<span data-ttu-id="e3303-688">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-688">Int32</span></span>|  
|<span data-ttu-id="e3303-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="e3303-689">INITIAL_SIZE</span></span>|<span data-ttu-id="e3303-690">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-690">Int32</span></span>|  
|<span data-ttu-id="e3303-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="e3303-691">NULLS</span></span>|<span data-ttu-id="e3303-692">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-692">Int32</span></span>|  
|<span data-ttu-id="e3303-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="e3303-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="e3303-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-694">Boolean</span></span>|  
|<span data-ttu-id="e3303-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="e3303-695">AUTO_UPDATE</span></span>|<span data-ttu-id="e3303-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-696">Boolean</span></span>|  
|<span data-ttu-id="e3303-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="e3303-697">NULL_COLLATION</span></span>|<span data-ttu-id="e3303-698">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-698">Int32</span></span>|  
|<span data-ttu-id="e3303-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e3303-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="e3303-700">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-700">Int64</span></span>|  
|<span data-ttu-id="e3303-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e3303-701">COLUMN_NAME</span></span>|<span data-ttu-id="e3303-702">String</span><span class="sxs-lookup"><span data-stu-id="e3303-702">String</span></span>|  
|<span data-ttu-id="e3303-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e3303-703">COLUMN_GUID</span></span>|<span data-ttu-id="e3303-704">Guid</span><span class="sxs-lookup"><span data-stu-id="e3303-704">Guid</span></span>|  
|<span data-ttu-id="e3303-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e3303-705">COLUMN_PROPID</span></span>|<span data-ttu-id="e3303-706">Int64</span><span class="sxs-lookup"><span data-stu-id="e3303-706">Int64</span></span>|  
|<span data-ttu-id="e3303-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="e3303-707">COLLATION</span></span>|<span data-ttu-id="e3303-708">Int16</span><span class="sxs-lookup"><span data-stu-id="e3303-708">Int16</span></span>|  
|<span data-ttu-id="e3303-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="e3303-709">CARDINALITY</span></span>|<span data-ttu-id="e3303-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="e3303-710">Decimal</span></span>|  
|<span data-ttu-id="e3303-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="e3303-711">PAGES</span></span>|<span data-ttu-id="e3303-712">Int32</span><span class="sxs-lookup"><span data-stu-id="e3303-712">Int32</span></span>|  
|<span data-ttu-id="e3303-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="e3303-713">FILTER_CONDITION</span></span>|<span data-ttu-id="e3303-714">String</span><span class="sxs-lookup"><span data-stu-id="e3303-714">String</span></span>|  
|<span data-ttu-id="e3303-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="e3303-715">INTEGRATED</span></span>|<span data-ttu-id="e3303-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="e3303-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3303-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3303-717">See Also</span></span>  
 [<span data-ttu-id="e3303-718">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e3303-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
