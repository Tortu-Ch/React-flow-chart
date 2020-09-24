# React Flow Chart


- [X] Dragabble Nodes and Canvas
- [x] Create curved links between ports
- [x] Custom components for Canvas, Links, Ports, Nodes
- [X] React state container
- [X] Update state on Select/Hover nodes, ports and links
- [x] Base functionality complete
- [X] Stable NPM version
- [X] Scroll/Pinch canvas to zoom
- [ ] Ctrl+z/Ctrl+y history
- [X] Read-only mode
- [ ] Redux state container
- [ ] Arrow heads on links
- [ ] Docs


This project aims to build a highly customisable, declarative flow chart library. Critically, you control the state. Pick from Redux, MobX, React or any other state managment library - simply pass in the current state and hook up the callbacks.

For example:

![demo](./images/demo.gif)

## Data Stucture

The flow chart is designed as a collection of Nodes, Ports and Links. You can specify your own custom properties, making this format quite flexible. See [types/chart.ts](./src/types/chart.ts). Note, nodes, ports and links should have a unique id.

#### Example

```ts

export const chart: IChart = {
  offset: {
    x: 0,
    y: 0,
  },
  scale: 1,
  nodes: {
    node1: {
      id: 'node1',
      type: 'output-only',
      position: {
        x: 300,
        y: 100,
      },
      ports: {
        port1: {
          id: 'port1',
          type: 'output',
          properties: {
            value: 'yes',
          },
        },
        port2: {
          id: 'port2',
          type: 'output',
          properties: {
            value: 'no',
          },
        },
      },
    },
    node2: {
      id: 'node2',
      type: 'input-output',
      position: {
        x: 300,
        y: 300,
      },
      ports: {
        port1: {
          id: 'port1',
          type: 'input',
        },
        port2: {
          id: 'port2',
          type: 'output',
        },
      },
    },
  },
  links: {
    link1: {
      id: 'link1',
      from: {
        nodeId: 'node1',
        portId: 'port2',
      },
      to: {
        nodeId: 'node2',
        portId: 'port1',
      },
    },
  },
  selected: {},
  hovered: {},
}

```

This will produce a simple 2 noded chart which looks like:

![Demo](./images/demo.png)

## Basic Usage

```bash
npm i @mrblenny/react-flow-chart
```

Most components/types are available as a root level export. Check the storybook demo for more examples.

```tsx
import { FlowChartWithState } from "@mrblenny/react-flow-chart";

const chartSimple = {
  offset: {
    x: 0,
    y: 0
  },
  nodes: {
    node1: {
      id: "node1",
      type: "output-only",
      position: {
        x: 300,
        y: 100
      },
      ports: {
        port1: {
          id: "port1",
          type: "output",
          properties: {
            value: "yes"
          }
        },
        port2: {
          id: "port2",
          type: "output",
          properties: {
            value: "no"
          }
        }
      }
    },
    node2: {
      id: "node2",
      type: "input-output",
      position: {
        x: 300,
        y: 300
      },
      ports: {
        port1: {
          id: "port1",
          type: "input"
        },
        port2: {
          id: "port2",
          type: "output"
        }
      }
    },
  },
  links: {
    link1: {
      id: "link1",
      from: {
        nodeId: "node1",
        portId: "port2"
      },
      to: {
        nodeId: "node2",
        portId: "port1"
      },
    },
  },
  selected: {},
  hovered: {}
};

const Example = (
  <FlowChartWithState initialValue={chartSimple} />
);
```

## Contributing

If you're interested in helping out, let me know. 

In particular, would be great to get a hand with docs and redux / mobx integrations.


## Development

```bash
npm install
npm run start:storybook
```
