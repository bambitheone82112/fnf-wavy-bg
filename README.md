# fnf-wavy-bg
this is the repository of wavy bg
you can make wavy bg if you see this.
# how do i do wavy bg?
simple. just do this on lua: function onCreatePost()
    makeLuaSprite('encoreBG', 'encoreBG', -750, 1500);
    addLuaSprite('encoreBG');
    addGlitchEffect('encoreBG', 2, 2);
    close(true);
    end
  and try the game and done.
  # how do i customize the mod?
  its to much thing that it wont fit to this. if you wanna add icon bounce, simple. just do this on your lua script: function onCreate()
    doTweenAlpha("iconDadFadeEventTween", "iconP2", 0, 0.001, "linear")
    makeAnimatedLuaSprite("iconBounce", "iconBounce", 520, 10)
    setLuaSpriteScrollFactor("iconBounce")
    addLuaSprite("iconBounce", true)
    setObjectOrder("iconBounce", 25)
    updateHitbox("iconBounce")
    setObjectCamera("iconBounce", "hud")
end

function onBeatHit()
    addAnimationByPrefix("iconBounce", "bounce", "pico bounce idle", 24, true)
end

function onUpdate(elapsed)
    function goodNoteHit(id, direction, noteType, isSustainNote)
        if getProperty("health") < 2 then
            removeLuaSprite("iconBounce", true)
            addedVariable = 820 - (600 * ((getProperty("health") / 2) * 100) * 0.01)
            makeAnimatedLuaSprite("iconBounce", "iconBounce", addedVariable, 10)
            setLuaSpriteScrollFactor("iconBounce")
            addLuaSprite("iconBounce", true)
            setObjectOrder("iconBounce", 25)
            updateHitbox("iconBounce")
            setObjectCamera("iconBounce", "hud")
        end
    end
    function noteMiss(id, direction, noteType, isSustainNote)
        if getProperty("health") > 0.01 then
            removeLuaSprite("iconBounce", true)
            addedVariable = 820 - (600 * ((getProperty("health") / 2) * 100) * 0.01)
            makeAnimatedLuaSprite("iconBounce", "iconBounce", addedVariable, 10)
            setLuaSpriteScrollFactor("iconBounce")
            addLuaSprite("iconBounce", true)
            setObjectOrder("iconBounce", 25)
            updateHitbox("iconBounce")
            setObjectCamera("iconBounce", "hud")
        end
    end
end

remember! put the icon bounce on mods/scripts folder
# how do i make modchart?
heres an example of modchart: function opponentNoteHit()
	triggerEvent('Add Camera Zoom', '0.005, 0.005', '0.005, 0.005');
end

function onUpdate(elapsed)

		for i=0,4,1 do
			   setPropertyFromGroup('opponentStrums', i, 'texture', 'NOTE_assets_galaxy')
		end
		for i = 0, getProperty('unspawnNotes.length')-1 do
			if getPropertyFromGroup('unspawnNotes', i, 'x') < 429 then
							setPropertyFromGroup('unspawnNotes', i, 'texture', 'NOTE_assets_galaxy');
			else
							setPropertyFromGroup('unspawnNotes', i, 'texture', 'NOTE_assets');
			end
		end
	end


