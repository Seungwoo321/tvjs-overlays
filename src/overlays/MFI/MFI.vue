<script>

import { Overlay } from 'trading-vue-js'

export default {
    name: 'MFI',
    mixins: [Overlay],
    methods: {
        meta_info() {
            return {
                author: 'StdSquad', version: '1.0.0',
                desc: 'Money Flow Index'
            }
        },
        use_for() { return ['MFI'] },
        calc() {
            return {
                props: {
                    length: { def: 14, text: 'Length' }
                },
                conf: { renderer: 'Range' },
                update: `
                    let hlc3 = ts((high[0] + low[0] + close[0]) / 3)
                    return mfi(hlc3, length)[0]
                `
            }
        }
    }
}
</script>
