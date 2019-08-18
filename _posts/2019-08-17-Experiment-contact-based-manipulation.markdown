---
layout: post
title:  "Cable shaping experiment configuration - Bazar robot"
date:   '2019-08-17'
categories: Robotics
---
## Video
[Link to the youtube video](https://www.youtube.com/watch?v=7CdNQ4R_wT0)

## Robot Configuration
# Gripper
    gripper_closing_distance: 0.005

# Vision
    image_file_extension: .png

    linear_interpolation_steps: 1
    segmentation_threshold: 45

    contact_image: bazar-experiment/images/contacts.png
    contact_roi:
        width: 1920
        height: 1080
        x: 0
        y: 0
    contact_color:
        lower_bound:
            hue: 195        # [0-360]
            saturation: 45  # [0-100]
            value: 40       # [0-100]
        upper_bound:
            hue: 260        # [0-360]
            saturation: 100  # [0-100]
            value: 100       # [0-100]

# Robot
    control_points:
      -   name: left_end-effector
          body_name: control-point_left
          ref_body_name: fixed_base
          limits:
              max_velocity: [0.2, 0.2, 0.2, 0.2, 0.2, 0.2]
              max_acceleration: [0.1, 0.1, 0.1, 0.1, 0.1, 0.1]
          gains:
              K_position_control_vector: [10, 10, 10, 10, 10, 10]
              Kp_force_control_vector: [0, 0, 0.1, 0, 0, 0]

      -   name: right_end-effector
          body_name: tool_right
          ref_body_name: fixed_base
          limits:
              max_velocity: [0.2, 0.2, 0.2, 0.2, 0.2, 0.2]
              max_acceleration: [0.1, 0.1, 0.1, 0.1, 0.1, 0.1]
          gains:
              K_position_control_vector: [10, 10, 10, 10, 10, 10]
              Kp_force_control_vector: [0, 0, 0.1, 0, 0, 0]


    observation_points:
      -   name: left_end-effector
          body_name: end-effector_left
      -   name: right_end-effector
          body_name: end-effector_right

    joint_groups:
      -   name: left_arm
          is_controlled: true
          priority: 1
          joints: [joint1_left, joint2_left, joint3_left, joint4_left, joint5_left, joint6_left, joint7_left]
          control_time_step: 0.005
          goal:
              position: [0, 0, 0, -1.57, 0, 0.3, 0]
          limits:
              max_velocity: [1, 1, 1, 1, 1, 1, 1]
              max_acceleration: [0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5]


      -   name: right_arm
          is_controlled: true
          priority: 1
          joints: [joint1_right, joint2_right, joint3_right, joint4_right, joint5_right, joint6_right, joint7_right]
          control_time_step: 0.005
          goal:
              position: [0, 0, 0, -1.57, 0, 0.3, 0]
          limits:
              max_velocity: [1, 1, 1, 1, 1, 1, 1]
              max_acceleration: [0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5]

      joint_controllers:
        -     joint_group: left_arm
              max_velocity: 0.5
              max_acceleration: 0.5

        -     joint_group: right_arm
              max_velocity: 0.5
              max_acceleration: 0.5


      task_space_controller:
          wrench_measure_enabled: true
          control_time_step: 0.005

      ik_controller:
          lambda_l1_norm_factor: 0.9
          # Possible values : 'StandardQP', 'SparseQP' or 'QP12'
          IK_type: StandardQP
