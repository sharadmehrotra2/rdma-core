set(MLX5_DEBUG "FALSE" CACHE BOOL
  "Enable expensive runtime logging options for the mlx5 verbs provider")
if (MLX5_DEBUG)
  add_definitions("-DMLX5_DEBUG")
endif()

set(MLX5_MW_DEBUG "FALSE" CACHE BOOL
  "Enable extra validation of memory windows for the mlx5 verbs provider")
if (MLX5_MW_DEBUG)
  add_definitions("-DMW_DEBUG")
endif()

rdma_shared_provider(mlx5 libmlx5.map
  1 1.3.${PACKAGE_VERSION}
  buf.c
  cq.c
  dbrec.c
  mlx5.c
  qp.c
  srq.c
  verbs.c
)

publish_headers(infiniband
  mlx5dv.h
)
