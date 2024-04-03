# Vue.js To-Do List Application

## Overview

This is a simple yet powerful to-do list application built using Vue.js. The application allows users to add, remove, and edit tasks, providing a seamless user experience for managing daily tasks.

## Features

- **Add Task**: Users can add a new task by typing into the input field and either pressing the enter key or clicking the "add to-do" button.
- **Edit Task**: Each task has an "Edit" button next to it. Clicking this button will make the task editable, allowing users to update the task description.
- **Remove Task**: Each task has a "Remove" button next to it. Clicking this button will remove the task from the list.
- **Clear Tasks**: Users can clear all tasks from the list by clicking the "clear" button.

## Code Structure

The application is built using Vue.js with the Composition API. The state of the tasks is managed using Vue's `ref` function, which creates a reactive reference.

The application's layout is defined in the `<template>` section, with the logic contained in the `<script setup>` section, and the styling in the `<style scoped>` section.

## Setup

To run this project locally, you will need to have Node.js and npm installed. After cloning the repository, install the dependencies by running `npm install`. You can then start the development server by running `npm run serve`.
