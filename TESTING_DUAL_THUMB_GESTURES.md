# Testing Guide: Dual-Thumb Simultaneous Gesture Input

## Prerequisites
- Android device with distinct multitouch support (most modern devices)
- FUTO Keyboard installed and enabled
- Gesture typing enabled in keyboard settings

## Test Cases

### 1. Single-Finger Gesture (Regression Test)
**Purpose**: Verify no regression in existing functionality

**Steps**:
1. Open any text input field
2. Swipe a single finger across keys to form a word (e.g., "hello")
3. Verify the word is recognized and inserted

**Expected Result**: ✓ Word suggestion appears and is inserted correctly

---

### 2. Dual-Thumb Simultaneous Gestures
**Purpose**: Test core dual-thumb functionality

**Steps**:
1. Open any text input field
2. Place both thumbs on the keyboard simultaneously
3. Swipe left thumb to form a word (e.g., "the")
4. While left thumb is still swiping, swipe right thumb to form another word (e.g., "quick")
5. Lift both thumbs

**Expected Result**: 
- ✓ Two distinct gesture trails visible
- ✓ Both words recognized
- ✓ Words inserted in correct order

---

### 3. Sequential Dual-Thumb Gestures
**Purpose**: Test gesture completion order

**Steps**:
1. Open any text input field
2. Start swiping with left thumb (e.g., "brown")
3. While left thumb is moving, start swiping with right thumb (e.g., "fox")
4. Lift left thumb first
5. Continue right thumb gesture and lift

**Expected Result**:
- ✓ Left gesture completes and word inserted when left thumb lifts
- ✓ Right gesture continues unaffected
- ✓ Right gesture completes when right thumb lifts
- ✓ Both words appear in the order they were started/completed

---

### 4. Hybrid Input (Tap + Swipe)
**Purpose**: Test mixed input modes

**Steps**:
1. Open any text input field
2. Start swiping with left thumb (e.g., "jumps")
3. While left thumb is swiping, tap a key with right thumb (e.g., "o")
4. Complete left thumb gesture

**Expected Result**:
- ✓ Tap registers correctly
- ✓ Gesture continues unaffected
- ✓ Both inputs work independently

---

### 5. Rapid Alternating Gestures
**Purpose**: Test switching between thumbs

**Steps**:
1. Open any text input field
2. Quickly swipe with left thumb (e.g., "the")
3. Immediately swipe with right thumb (e.g., "lazy")
4. Immediately swipe with left thumb (e.g., "dog")

**Expected Result**:
- ✓ All three words recognized
- ✓ No interference between gestures
- ✓ Visual trails display correctly

---

### 6. Visual Trail Verification
**Purpose**: Verify visual feedback

**Steps**:
1. Open any text input field
2. Swipe slowly with both thumbs simultaneously
3. Observe the gesture trails

**Expected Result**:
- ✓ Two distinct trails visible
- ✓ Trails follow finger movements accurately
- ✓ Trails fade appropriately after gesture completes

---

### 7. Long Text Entry
**Purpose**: Test practical usage

**Steps**:
1. Open any text input field
2. Use dual-thumb gestures to type a full sentence
3. Alternate between single-thumb and dual-thumb input

**Expected Result**:
- ✓ Can comfortably type with both input styles
- ✓ No crashes or hangs
- ✓ Text appears correctly

---

## Performance Testing

### Responsiveness
- Gesture recognition should feel instant
- No lag when switching between thumbs
- Visual trails should update smoothly

### Memory Usage
- No memory leaks during extended dual-thumb use
- App remains responsive after many gestures

## Edge Cases to Test

1. **Three fingers**: What happens if user tries to gesture with more than 2 fingers?
   - Expected: System handles gracefully, typically ignoring extra touches

2. **Very fast gestures**: Extremely quick swipes
   - Expected: Words still recognized correctly

3. **Overlapping gesture paths**: When thumbs cross paths
   - Expected: Each gesture tracked independently

4. **Gesture cancellation**: Starting a gesture then pressing back/home
   - Expected: Gestures cancelled cleanly

## Known Limitations

- **Legacy devices without distinct multitouch**: Will continue to use single-finger mode
- **First use**: Users may need to adjust to dual-thumb typing technique
- **Small screens**: May be challenging on phone-sized devices (more suitable for tablets)

## Reporting Issues

When reporting issues, please include:
1. Device model and Android version
2. Steps to reproduce
3. Expected vs actual behavior
4. Screenshots or screen recording if possible
5. Whether device has distinct multitouch (check: Settings > About Phone > Build Number)

## Success Criteria

✓ All regression tests pass (single-finger still works)  
✓ Can swipe with both thumbs simultaneously  
✓ Each gesture produces independent word suggestions  
✓ Visual trails display for both gestures  
✓ No crashes or performance degradation  
✓ Feels natural and responsive to use
