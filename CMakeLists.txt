#
# Copyright (c) 2022 Laird Connectivity LLC
#
# SPDX-License-Identifier: LicenseRef-LairdConnectivity-Clause
#
if(CONFIG_LCZ_BLE_GW_DM)

# Add framework ID and msgcode files
add_fwk_id_file(${CMAKE_CURRENT_SOURCE_DIR}/src/framework_config/fwk_ids.h)
add_fwk_msgcode_file(${CMAKE_CURRENT_SOURCE_DIR}/src/framework_config/fwk_msg_codes.h)

zephyr_include_directories(include)
zephyr_include_directories(src/framework_config)

zephyr_sources(src/lcz_ble_gw_dm_task.c)
zephyr_sources_ifdef(CONFIG_ATTR src/ble_gw_dm_device_id_init.c)
zephyr_sources_ifdef(CONFIG_LCZ_BLE_GW_DM_MEMFAULT src/memfault_task.c)
zephyr_sources_ifdef(CONFIG_BT src/ble_gw_dm_ble.c)
zephyr_sources_ifdef(CONFIG_LCZ_BLE_GW_DM_TELEM_LWM2M src/lwm2m_telemetry.c)
zephyr_sources_ifdef(CONFIG_FSU_ENCRYPTED_FILES src/lcz_ble_gw_dm_file_rules.c)
zephyr_sources_ifdef(CONFIG_MCUMGR src/lcz_ble_gw_dm_smp_rules.c)

endif()
