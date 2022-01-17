# flip-vehicle-in-radialmenu 
Deleted User 5bd78114 — 11/17/2021

flip vehicle with qb-radialmenu

https://youtu.be/p45FbdDdhE8

YouTube

Cường PlayGirl







go to qb-radialmenu/client/main.lua

paste this code

RegisterNetEvent('qb-radialmenu:client:flipvehicle', function()

    local ped = PlayerPedId()

    local coords = GetEntityCoords(ped)

    local vehicle = GetClosestVehicle(coords.x, coords.y, coords.z, 5.0, 0, 71)

    if DoesEntityExist(vehicle) then

        exports['progressbar']:Progress({

            name = "flipping_vehicle",

            duration = 5000,

            label = "Fliping Vehicle...",

            useWhileDead = false,

            canCancel = true,

            controlDisables = {

                disableMovement = true,

                disableCarMovement = true,

                disableMouse = false,

                disableCombat = true,

            },

            animation = {

                animDict = "random@mugging4",

                anim = "struggle_loop_b_thief",

                flags = 49,

            }

        }, function(status)

            SetVehicleOnGroundProperly(vehicle)

        end)

    else

        QBCore.Functions.Notify('No vehicle nearby', 'error', 2500) 

    end

end)

and config.lua

{

    id = 'flipvehicle',

    title = 'flip vehicle',

    icon = 'truck-pickup',

    type = 'client',

    event = 'qb-radialmenu:client:flipvehicle',

    shouldClose = true

 }
