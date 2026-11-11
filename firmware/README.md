# Firmware

Two STM32CubeMX + Keil MDK-ARM projects and their prebuilt images.

```text
firmware/
├── robot/                  # STM32F407VET6 · robot body
│   ├── Task/               # FreeRTOS application tasks (project logic)
│   ├── Hardware/           # Device drivers: NRF24L01, WIT IMU, OLED, soft I²C …
│   ├── Core/               # CubeMX-generated init code
│   ├── Drivers/            # STM32 HAL / CMSIS (vendor)
│   ├── Middlewares/        # FreeRTOS (vendor)
│   ├── MDK-ARM/            # Keil project
│   └── RollingRobot.ioc
├── controller/             # STM32F103C8T6 · handheld remote
│   ├── Hardware/           # NRF24L01, OLED
│   ├── Core/ Drivers/ MDK-ARM/
│   └── Controller.ioc
└── prebuilt/
    ├── rolling-robot.hex
    └── controller.hex
```

| Target | MCU | Keil project | Responsibility |
| --- | --- | --- | --- |
| Robot | STM32F407VET6 | [`robot/MDK-ARM/RollingRobot.uvprojx`](robot/MDK-ARM/RollingRobot.uvprojx) | Sensing, pressure regulation, gait control, servo actuation, telemetry |
| Controller | STM32F103C8T6 | [`controller/MDK-ARM/Controller.uvprojx`](controller/MDK-ARM/Controller.uvprojx) | User input, status display, wireless commands |

## Prebuilt images

| File | Target | SHA-256 |
| --- | --- | --- |
| `prebuilt/rolling-robot.hex` | STM32F407VET6 | `288effec6bad4e7ef87aea7a6e5c70c6d34b9f251354cafb380e96b99d466670` |
| `prebuilt/controller.hex` | STM32F103C8T6 | `15e107987f9907d8fa387220b6d4a9f74bc74f0a82418485e1e0af88ece7027e` |

They only run on boards matching the pin assignments in the `.ioc` files.

## Build hygiene

Keil outputs (`.o`, `.axf`, `.map`, listings, dependency files) and per-user `.uvguix.*` / `.uvoptx` settings are git-ignored. Only `prebuilt/*.hex` is tracked.
