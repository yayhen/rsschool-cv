# Name and surname 
Papok Yayhen
# Email
mlpoknwow@gmail.com
# About me
I was born on April 23, 1993. 
# Skills
A basic level of HTML, CSS, Javascript. I can work a little with React, Reedux. 
# Code examples
below is an excerpt from the reducer of my cellular automaton implementation:
```
import { NEXT_TURN } from "./types";
import { ADD_UNIT } from "./types";
import { RANDOM_FILLING } from "./types";

const initialState = {
    mapCondition: [[0,0,0,0,0], [0,0,0,0,0], [0,0,0,0,0], [0,0,0,0,0], [0,0,0,0,0]],
    XDimension: 21,
    YDimension: 21
}

const initState = () => {
    let arr = [];
    for (let i=0; i<initialState.XDimension; i++) {
        arr[i] = new Array(initialState.YDimension);
    }
    console.log(initialState.YDimension)
    console.log(arr)
    for (let i=0; i<initialState.XDimension; i++) {
        for (let j=0; j<initialState.YDimension; j++) {
            arr[i][j] = 0;
        }
    }
    
    return {
        XDimension: initialState.XDimension,
        YDimension: initialState.YDimension,
        mapCondition: arr
    }
}

export const fieldReduser = (state = initState(), action) => {
    switch (action.type) {
        case (ADD_UNIT):
            return {...state, mapCondition: state.mapCondition.map( (item, index) => {
                let tmpArr = item;
                    for(let i=0; i<state.YDimension; i++) {
                        if(action.payload.x==index && action.payload.y == i) {
                            tmpArr[i] = 1;
                        }
                    }
                return tmpArr
                }
            )};
        case (NEXT_TURN):
            let nextMapCondition;
            let tmpMap;
            nextMapCondition = state.mapCondition.map(item => {
                return [...item]
            })
            tmpMap = nextMapCondition.map(item => {
                return [...item]
            })   
            let sumLives = 0;
            for (let i=0; i<state.XDimension; i++) {
                for (let j=0; j<state.YDimension; j++) {
                    sumLives = 0;
                    if (j!=0) if (tmpMap[i][j-1] == 1) sumLives++;
                    if (j!=state.YDimension-1) if (tmpMap[i][j+1] == 1) sumLives++;
                    if (i!=0) if (tmpMap[i-1][j] == 1) sumLives++;
                    if (i!=0 && i!=0) if (tmpMap[i-1][j-1] == 1) sumLives++;
                    if (i!=0 && j!=state.YDimension-1) if (tmpMap[i-1][j+1] == 1) sumLives++;
                    if (i!=state.XDimension-1) if (tmpMap[i+1][j] == 1) sumLives++;
                    if (i!=state.XDimension-1 && j!=0) if (tmpMap[i+1][j-1] == 1) sumLives++;
                    if (i!=state.XDimension-1 && j!=state.YDimension-1) if (tmpMap[i+1][j+1] == 1) sumLives++;
                    if (tmpMap[i][j] == 0) {
                        if (sumLives == 3) nextMapCondition[i][j] = 1
                            else nextMapCondition[i][j] = 0
                    }
                    if (tmpMap[i][j] == 1) {
                        if (sumLives == 2 || sumLives == 3) nextMapCondition[i][j] = 1
                            else nextMapCondition[i][j] = 0
                    }
                }
            }
            return {...state, mapCondition: state.mapCondition.map((item, index) => {
                return nextMapCondition[index]
            })}
        case (RANDOM_FILLING):
        let density = Math.random();
            return {...state, mapCondition: state.mapCondition.map((item, index) => {
                let tmpArr = item;
               for(let i=0; i<state.YDimension; i++) {
                   if (Math.random() > 1 - density) {
                       tmpArr[i] = 1;
                   } else tmpArr[i] = 0;
               } 
               return tmpArr;
            })}
        default: 
            return state
    }
}
```

# Experience
# Education
In 2019 I graduated from the Faculty of Physics of the Belarusian State University with a degree in physics of nanomaterials and nanotechnologies.
# Current English 
A1
