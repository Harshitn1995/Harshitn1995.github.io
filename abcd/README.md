# StencilComponent

**File:** `stencil.component.ts`  
**Location:** `src/app/modules/engage/canvas-new/canvasComponent/stencil/`

======================================================================================================================

## Overview

- The `StencilComponent` serves as a palette of available node types for a visual flow editor.
- Users can drag nodes from the stencil onto the canvas to visually construct flows.
- Nodes are organized into groups by block type (e.g., trigger, action, condition, flow).
- Each group can be collapsed or expanded to streamline navigation and enhance user experience.
- The component improves usability for large node libraries by supporting group collapsing.
- Drag-and-drop functionality enables seamless integration with the canvas area.

======================================================================================================================

## Component Metadata
 ____________________________________________
| Property     | Value                       |
|--------------|-----------------------------|
| **Selector** | `app-stencil`               |
| **Imports**  | `CommonModule`              |
| **Template** | `stencil.component.html`    |
| **Style**    | `stencil.component.css`     |

======================================================================================================================

## Dependencies

- **NodeCollectionService:**  
  Provides access to the available node types and their metadata.

======================================================================================================================

## Properties
 __________________________________________________________________________________________________________________
| Name             | Type                         | Description                                                    |
|------------------|----------------------------- |----------------------------------------------------------------|
| `nodes`          | `NodeModel[]`                | List of all available nodes (not directly used in this file)   |
| `collapsedGroups`| `{ [key: string]: boolean }` | Tracks collapsed/expanded state for each node group            |

**Default `collapsedGroups`:**
```typescript
{
  trigger: true,
  action: true,
  condition: true,
  flow: true
}
```

======================================================================================================================

## Methods

### `getNodesByBlockType(blockType: string): NodeModel[]`

Returns all nodes of a given block type by delegating to `NodeCollectionService`.

- **Parameters:**  
  - `blockType` (`string`) : The type/category of node (e.g., 'trigger', 'action', 'condition', 'flow').
- **Returns:**  
  - `NodeModel[]`          : Array of nodes matching the block type.

======================================================================================================================

### `onDragStart(event: DragEvent, node: any): void`

Handles the drag start event for a node in the stencil.  
Serializes the node data and attaches it to the drag event for use in the canvas drop handler.

- **Parameters:**  
  - `event` (`DragEvent`) : The drag event.  
  - `node` (`any`)        : The node being dragged.

======================================================================================================================

### `toggleGroup(group: string): void`

Toggles the collapsed/expanded state of a node group in the stencil.

- **Parameters:**  
  - `group` (`string`)    : The group name to toggle.

======================================================================================================================

## Usage Example

```html
<div *ngFor="let group of ['trigger', 'action', 'condition', 'flow']">
  <div (click)="toggleGroup(group)">
    {{ group | titlecase }}
    <span>{{ collapsedGroups[group] ? '+' : '-' }}</span>
  </div>
  <div *ngIf="!collapsedGroups[group]">
    <div *ngFor="let node of getNodesByBlockType(group)"
         draggable="true"
         (dragstart)="onDragStart($event, node)">
      {{ node.label }}
    </div>
  </div>
</div>
```

======================================================================================================================

## Notes

- The stencil is typically displayed as a sidebar in a flow editor UI.
- Drag-and-drop integration allows users to add nodes to the canvas.
- Group collapsing improves navigation for large node libraries.
- Relies on `NodeCollectionService` for node metadata and filtering.

======================================================================================================================

## Related Files

| File                         | Description                                 |
|------------------------------|---------------------------------------------|
| `stencil.component.html`     | The template for rendering the stencil UI.  |
| `node.model.ts`              | Defines the `NodeModel` interface.          |
| `node-collection.service.ts` | Provides node data and filtering logic.     |

======================================================================================================================
