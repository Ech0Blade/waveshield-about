# waveshield-about

# How Bypass ws Guard Fivem qb/qbx/esx Core with macho

# Method 1
for i = 1, 2 do
    MachoInjectResource2(3, 'WaveShield', [[
        error('wpggtriggerhere :(')
    ]])
end

# Method 2

MachoInjectResourceRaw('unsaferesource', [[
    CreateVehicle('bmx', GetEntityCoords(PlayerPedId()), 0.0, true, false)
    print('hello motha fucka')
    TriggerEvent('esx_ambulancejob:revive')
    --TriggerServerEvent('SERVER_EVENT')
]])

# Method 3

MachoInjectResourceRaw('monitor', [[
    local function SafeWrap(setFunc)
        return function(...)
            return setFunc(...)
        end
    end

    local SafeThread = SafeWrap(CreateThread)
    local SafeCVehicle = SafeWrap(CreateVehicle)
    local SafeCTrigger = SafeWrap(TriggerEvent)
    local SafeSTrigger = SafeWrap(TriggerServerEvent)

    SafeThread(function()
        SafeCVehicle('bmx', GetEntityCoords(PlayerPedId()), 0.0, true, false)
        print('YO')
        SafeCTrigger('esx_ambulancejob:revive')
        --SafeSTrigger('SERVER_EVENT')
    end)
]])
