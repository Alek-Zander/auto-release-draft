# Actions taken

## The Walking Skeleton

"A tiny imnplementation of the system that performs a small end-to-end function"
### To build a Walking Skeleton



1. Modify metada information, Open and modify action.yml
    - Add name: 'Auto Release Draft' 
    - description: 'Drafts a GitHub release with changes introduced by a newly created tag
    - author: 
    - remove input data "myInput"
    - Leaving as is the runs section
2. modify package.json package Metadata
    - Change name, description, pository url, and author.
    - Look at the dependencies:
3. modify src\main.ts
    - Remove:  
        ```const ms: string = core.getInput('milliseconds')
        core.debug(`Waiting ${ms} milliseconds ...`) // debug is only output if you set the secret `ACTIONS_STEP_DEBUG` to true

        core.debug(new Date().toTimeString())
        await wait(parseInt(ms, 10))
        core.debug(new Date().toTimeString())

        core.setOutput('time', new Date().toTimeString())```
    - Remove:  
        ```import {wait} from './wait'```  
        ```if (error instanceof Error)```
4. Modify main.test.ts  
        ```
        import * as core from '@actions/core'
        import { run } from '../src/main'

        jest.mock('@actions/core')

        describe('When running the action', () => {
        const fakeSetOutput = core.setOutput as jest.MockedFunction<Typeof core.setOutput>

        test('it should set the release-url ouput parameter', async () => {
            await run()
                expect(fakeSetOutput).toHaveBeenCalledWith('release-url',expect.anything())
        })
        })
        ```